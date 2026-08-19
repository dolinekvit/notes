`position: absolute` positions an element relative to a positioned parent.
`position: fixed` positions an element relative to the viewport unless a new Containing Block is formed.
`position: absolute` elements will be clipped inside the `overflow: hidden` elements.
`position: fixed` elements can escape the `overflow: hidden` problem, but they can't escape the Stacking Context.
Nothing can escape the Stacking Context. If you are trapped there, it's game over.
Stacking Context is formed by setting `position` and `z-index`, by setting `translate`, and so many other things.
Portals allow you to easily render some elements, like modal dialogs, outside of their current DOM position so that the Stacking Context doesn't trap them.
When using Portals, the rules are:
- What happens in React stays within the React hierarchy.
- What happens outside of React follows DOM structure rules.
