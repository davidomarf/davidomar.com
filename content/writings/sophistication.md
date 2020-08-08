---
title: "When sophistication gets in the way"
excerpt:
  Or how I spent a whole day of slow debugging due to an error I introduced by
  trying to "prove my worth".
date: 2020-07-07T08:10:12-05:00
code: true
toc: true
comments: true
draft: false
---

Last week in my job, we got a pretty weird issue in one of our projects. Some
internal links (that were handled using Angular Router) were broken. They all
redirected us to the default route.

But it was only noticed in the optimized production application, not in the
development server. So we never noticed until it was on staging.

---

Fixing it was pure hell because building the optimized app is slower. Way
slower.

For every change I decided was worthy of trying, I had to wait around **2
minutes** to see it reflected in the page.

After several hours, I finally found what was happening. And I felt dumb. All
those posts suggesting to keep things simple and to avoid snobbery, suddenly hit
close to home.

I'll briefly describe our necessities and reasoning to understand what led
~~us~~ me to firstly introduce that bug.

## App Routing

In many of our modules with routing, we have a list of children routes defined
like this:

```ts
children: [
  {
    path: "first/:id",
    loadChildren: () =>
      import("./first/first.module").then((m) => m.FirstModule)
  },
  {
    path: "second/:id",
    loadChildren: () =>
      import("./second/second.module").then((m) => m.SecondModule)
  }
  // ... more children
];
```

These components were a list of items, and clicking one item opened a sidebar
with details. But that was also a route:

`/items -> /items/details/:id`

The app lived happily for many months with routes like that.

But then we had to add a new component `BottomBar` that was omnipresent. Even
when said sidebar was open.

The style and behavior of `BottomBar` depended on whether the current route was
to be rendered as a sidebar.

In our example, `/items` is not a sidebar, but `/items/details/:id` is.

## Route data

The easiest way to do that was adding some extra data to those routes using a
`data` property. An example in the Angular docs is in the second code block
after [Adding routable animations][angular-docs].

```ts
{
  path: "first/:id",
  loadChildren: () =>
    import("./first/first.module").then((m) => m.FirstModule),
  data: {
    isSidebar: true
  }
},
```

So now we could use Router events to check if the current route was a sidebar:

```ts
export class AppComponent implements OnInit, OnDestroy {
  // Subscription for the router events
  private checkSidebarSubscription = Subscription.EMPTY;

  constructor(
    private readonly router: Router,
    private readonly route: ActivatedRoute
  ) {}

  ngOnInit() {
    // When a NavigationEnd event is emmited,
    // check if the final route is a sidebar
    this.checkSidebarSubscription = this.router.events
      .pipe(filter((e: Event) => event instanceof NavigationEnd))
      .subscribe(this.checkIsSidebar);
  }

  ngOnDestroy() {
    this.checkSidebarSubscription.unsubscribe();
  }

  private checkIsSidebar(): boolean {
    let current = this.route.snapshot;
    // Go through all the `firstChild`s until one has `isSidebar`
    // If no firstChild has `isSideBar`, return false.
    while (current.firstChild) {
      if (current.firstChild.data?.isSidebar) {
        return true;
      } else {
        current = current.firstChild;
      }
    }
    return false;
  }
}
```

That worked wonders. That kept our app working just fine 👌.

But I had to get creative.

> How could I let my code be so unpolished? So dirty and unglamorous. Who would
> be proud of hardcoding `data: { isSidebar: true }` for every children route in
> a module with three routes? Not me, **I want to show whomever reads my code
> that I'm sophisticated**.

(That's how I picture my own brain when I decided to do the following)

## Mapping > Hardcode

I noticed that some components that were supposed to be sidebars, had more than
one children.

When you have one, or even two, it made sense to write the `data` prop to each
of them.

But when having more, maybe you could just map the children array to
"programatically" add it to all the routes:

```ts
children: [
  // ... 2+ children with {path: "", loadChildren: () => {}}
].map((e: Route) => ({ ...e, data: { isSideBarOpen: true } }));
```

And it kept working wonders!

So I confidently commit and push my changes. The code gets reviewed and my
changes approved. Pipelines get run, issues get closed, and we call it a day.

A couple of days later, we update `staging` for QA to test our changes, and
right after, they tell us the app is **broken**. **Big time broken**.

And then the story from the beginning... The boring hours of waiting for the app
to compile. Of tracking commits until finding the one that produced the error.
Of unfruitful Google searches.

And finally, the funny realisation of what I did to put myself in that
situation.

## The Aftermath

I don't know yet why our configuration for optimized production builds didn't
work with `mapped` routes.

The error that we were getting when navigating was
`Navigation ID is not equal to the current router navigation id`.

I looked for solutions for that error, but no proposed solution seem to even
suggest there was an error with the `children` property.

I think it's a weird error. I don't know if I skipped a chunky part of the
documentation on Routing, or if it's not even documented.

I'm interested on learning more about Routing in general. For example, if you
have an Angular project with Routing, try one of these:

1. Subscribe to router events, and print each event, or
2. [Enable Tracing][tracing].

My socks were blown off when I saw all the events that get logged.

This was one of my favorite learning experiences. Be humble and don't try to do
something just because you know how to. Don't try to impress anyone. Specially
if that could cost your code some readability.

[angular-docs]: https://angular.io/guide/router#adding-routable-animations
[tracing]: https://angular.io/api/router/ExtraOptions#properties
