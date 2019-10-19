# Route

Route uses the original
[react-router `<Route />`](https://reacttraining.com/react-router/web/api/Route).
It wraps the children with a transition component based on
[`<Transition />`](https://reactcommunity.org/react-transition-group/transition)
   and [`<CSSTransition />`](https://reactcommunity.org/react-transition-group/css-transition).

Must be used inside [`<Navigation />`](/docs/navigation) to allow [`<Link />`](/docs/link)
to consume context.

Comes with some default css class that you can disable or chain with
your custom classes.

## Props
### `children` (required)

Propably your 'page' component. I recommend you to use [`<Screen />`](/docs/screen)
to wrap your pages. Or pass in the `screen` prop to automatically
wrap.

type: `union(func|node)`


### `className`

Div container className. A string or a function returning a string.
If not `disableStyle`, this className will be chained to
`react-tiger-transition--route` or `react-tiger-transition--fixed`.

type: `union(string|func)`


### `containerProps`

Props passed to div container.

type: `object`


### `disableStyle`

Disable default styles applied to the div container. You can
still use className to set your own styles.

type: `bool`
defaultValue: `false`


### `fixed`

In case you want a route to render only a component like appbars,
this is a shorthand, but you still need to set positioning and height.
The only thing `fixed` does is not setting your `<route />` to fullscreen,
like a regular route page.

type: `bool`
defaultValue: `false`


### `screen`

Autimatically wraps route child with `<Screen />`.

type: `bool`
defaultValue: `false`


### `screenProps`

If `screen` prop is true, you can pass props to it.

type: `object`
defaultValue: `{}`


### `transitionProps`

Props passed to [`<Transition />`](https://reactcommunity.org/react-transition-group/transition)
or [`<CSSTransition />`](https://reactcommunity.org/react-transition-group/css-transition).
Usually you don't need to worry about this. If you pass `appear`, the
appearing animation is the default one defined in [`<Navigation />`](/docs/navigation).
Props defined here have higher priority than `globalTransitionProps`
defined in [`<Navigation />`](/docs/navigation).

type: `object`


\*Any other prop is passed to
[react router `<Route />`](https://reacttraining.com/react-router/web/api/Route).

## Example
```javascript
import { BrowserRouter as Router} from "react-router-dom";

import {
  Navigation, // Route needs context from Navigation
  Route,
  Screen,
  Link,
} from "react-tiger-transition";

<Router>
  <Navigation>
    <Route exact path="/a" >
      <Screen>
        <PageA />
      </Screen>
    </Route>

    <Route exact path="/b" screen children={<PageB />} />

    { moreRoutes }

  </Navigation>
</Router>
```

\*Refer to [transitions API](/docs/transitions), for more details about
transitions.