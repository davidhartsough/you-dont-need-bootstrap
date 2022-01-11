# You don't need Bootstrap

**Why you might not need any CSS framework for smaller websites or apps**

## When you need it, when you don't

Bootstrap (swept the internet back in blah blah blah and became the most widely used blah blah — history lesson blah blah). It's extremely popular blah blah. But just because something is extremely popular, doesn't mean that you should blindly assume that you need it in all of your projects. As with all things in life, everything can be great for some purposes but bad at other times. Sometimes a CSS framework is perfect for a project; sometimes it's overkill. The key with learning about new resources is to build up a solid discernment of when those resources are most useful. Every resource serves a particular purpose for particular projects. Trying to _always_ use the same resources in _every_ project is like trying to use a hammer for every home remodeling project. Sometimes you need a screwdriver; sometimes you just need a crowbar. This lesson is aimed at giving you the crowbar basics of the CSS framework hammer. If you're just trying to remove some nails, you don't need the front side of the hammer. With Bootstrap and other CSS frameworks, they give you a rather large toolbox of CSS, HTML, and JS resources. This pool of resources can be overkill for most projects that are relatively small and simple. Let's talk "data".

### How big?

Bootstrap v4 minified is 160 KB of CSS + 60 KB of JS + 71 KB of jQuery + 21 KB of Popper.js for a total of 312 KB. (Materialize is 142 KB of CSS + 181 KB of JS = 323 KB. And Foundation is 145 KB of CSS + 503 KB of JS + 272 KB of jQuery = 916 KB.)

#### Is that a big deal?

Not really... But! I'm here to tell you that you probably just need about 200 lines of CSS or less at < 5 KB. That means your CSS is guaranteed to load virtually immediately on even the slowest of connections (< 0.7 seconds on 56 kbps), whereas Bootstrap might take 45 seconds to load on the slowest connection (56 kbps). We're talkin' 1% the file size downloaded.

Again, this isn't a really big deal for most people and most projects, so I wanna talk about another reason why you might not need it:

### Craftsmanship

I'm going to use this word, "craftsmanship", as an excuse for being rather particular about my projects and feeling a deep sense of satisfaction knowing that everything about my project is intentional and specifically created with good reason. That just means that I personally don't like to use Bootstrap or a large CSS framework like that when I really want to be in complete control over my project's styling. With great control comes great responsibility, but that can be gratifying for me when I'm trying to build a new project from scratch. I love to have complete control over it and know that I hand crafted every piece of the project. There's something to be said about the pride one can have in a project that is crafted "by hand". When I know exactly how everything works because I took the time to write almost every line of code myself, I feel my proudest. "That's priceless."

## The stuff you'll always need

### 1. Normalize.css

[Normalize.css](https://necolas.github.io/normalize.css/) (also [see the source on GitHub](https://github.com/necolas/normalize.css))

> **Normalize.css** makes browsers render all elements more consistently and in line with modern standards. It precisely targets only the styles that need normalizing.

Basically it just ensures that every base HTML element you use will have the same base CSS styles across every browser. So it eliminates most of the dilemma of dealing with different browsers and browser-specific styles. This should go before all your other CSS to provide that perfect blank slate and solid foundation (of knowing what to expect — the more deterministic the better).

See [my simplified version of it](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/normalize.slim.css).

### 2. Intuitive box-sizing

```css
html {
  box-sizing: border-box;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
```

### 2. CSS for `body`

The `body` is where you set the base styles for all other elements to inherit. You'll want to set your basic theme here. Choose a background color and a font (family, size, weight, height, etc).

Try to avoid a stark white background for most websites. It's not easy on the eyes. But fair warning: there's a very fine line between "bland and ugly white" and "gray and gloomy off-white". You'll have to ride those lines and see for yourself. I find that `#FAFAFA` usually does just the trick. It's just one step in the right direction. (It's actually 2% less "light" than pure white, according to its equivalent HSL value: `hsl(0, 0%, 98%)`.)

Also, _(personal opinion here)_ serif fonts are lame and for books — not for websites. It feels weird to see serif fonts on screens. Some say it's technically better/easier for reading, but it's not pretty. If your website has a lot of written content, maybe consider the best fonts that e-readers have chosen. (I read once that Amazon did research for its Kindle to discover the best typeface for reading. I'll have to revisit that. Maybe you'll find what I'm talking about. But follow the research.) Otherwise, if your website has minimal sections of written content and rarely has lengthy paragraphs and paragraphs of text, then go for what's more aesthetically pleasing: `sans-serif`.

In fact, most operating systems default to a sans-serif font for everything. You should probably keep your website's font aligned with the device's default font, to keep things consistent. To do this, you'll actually want to target all the best sans-serif fonts from every device, in the order of coolest, best-looking, and most-likely-to-override-anyway. This ensures that you'll get the best sans-serif font on every device. For example, if you just chose "Roboto" (the sexiest of fonts), your website would have access to it on Android devices but wouldn't have access to it on iOS devices, so you'd have to manually import it from Google fonts. If you list all the defaults instead, the device will automatically choose its best sans-serif font for you, based on what it already has available (system fonts).

"Sans-serif is so hot right now."

```css
body {
  /* Personal preferences */
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto",
    "Helvetica Neue", Arial, sans-serif;
  background-color: #fafafa;
  /* Basics from normalize.css */
  margin: 0;
  -webkit-text-size-adjust: 100%;
  font-size: 1rem;
  font-weight: 400;
  /*
    Normalize.css sets line-height to 1.15 as a standard,
    but I prefer 1.5 as the base for all text,
    because it's a bit more readable and spacious.
  */
  line-height: 1.15;
}
```

### 3. CSS for `main`

I prefer to use the `main` element as my base container, because I like it semantically, but you can use whatever you want. (Just make sure it's a block element.)

This CSS is a pretty standard way to ensure that your content doesn't stretch out forever on super wide screens. (A bad example of this is Wikipedia; I love the site, but it looks bad on large/wide screens and becomes more difficult to read all the way across the screen.) It's easier to read text that doesn't extend too far and wide.

"Keep it together."

```css
main {
  /* I prefer to put margin at the bottom to scroll past the bottom of the content for readability. */
  margin: 0 auto 4rem;
  /* This width is an arbitrary example. Choose your own value. */
  max-width: 42rem;
}
```

### 4. CSS for `section`

I prefer to wrap my content in a section element inside my main element. Again, it's just semantics for me — use whatever you wish.

Since we did away with the `body`'s default `margin: 10px`, we need to bring that space back here so you don't have your content butting up against the edge of the screen. Personally, I like to add about `1rem` of `padding` for smaller screens, while I have `2rem` for larger screens, because mobile devices (phones) can't always afford to be as liberal with their spacing (when there's limited room to fit the content on the screen). Hence why you see the media query with a breakpoint.

"Spacing is sexy."

```css
section {
  /* This value is a personal preference. */
  padding: 1rem;
}
/* This is an arbitrary breakpoint. Choose your own value. */
@media screen and (min-width: 480px) {
  section {
    padding: 2rem;
  }
}
```

### 5. CSS for Typography

"Thinner for the winner."

```css
/* Basic text */
/* These values are a personal preference. */
h1 {
  font-size: 2.5rem;
}
h2 {
  font-size: 2rem;
}
h3 {
  font-size: 1.75rem;
}
h4 {
  font-size: 1.5rem;
}
h5 {
  font-size: 1.25rem;
}
h1,
h2,
h3,
h4,
h5 {
  margin: 0 0 0.5rem 0;
  /* Personally, I prefer lightweight headings. */
  font-weight: 300;
}
p {
  margin: 0 0 0.5rem 0;
  font-weight: 400;
}
/* Links */
a {
  text-decoration: none;
  /* This color is a personal preference. */
  color: #146eeb;
}
a:hover {
  text-decoration: underline;
}
/* Lists */
ul,
ol {
  margin: 0.5rem 0 1rem;
  padding-inline-start: 2rem;
}
ul ul,
ul ol,
ol ul,
ol ol {
  margin: 0;
}
```

See [the base.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/base.css).

## Stuff you'll _often_ want

Before diving totally into different types of common "components", I wanna touch on picking a "theme" real quick:

In the section above, I made all `a` tags the color `#146eeb`. That's just a nice blue I've picked out for myself. You can pick whatever you'd like. Here's <span style="color: #146eeb">how this blue looks</span>. You like?

<div style="background-color: #146EEB; color: #fff; text-align: center; padding: 1rem; margin: auto; max-width: 100px;">#146EEB</div>

(This doesn't render a blue box on GitHub, but you can check it out on your own.)

### List groups

AKA "collections"

```css
.list {
  /* Choose your favorite color. */
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  margin: 0.75rem 0;
  overflow: hidden;
}
.list-item {
  /* Choose how big you want each row to be. */
  padding: 0.5rem 0.75rem;
  border-bottom: 1px solid #ddd;
  background-color: #fff;
}
.list-item:last-child {
  border-bottom: none;
}
```

See [the list.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/list.css).

### Buttons

```css
/* Buttons */
/* Base */
.button,
button,
input[type="submit"],
input[type="reset"],
input[type="button"] {
  display: inline-block;
  padding: 0.5rem 0.75rem;
  cursor: pointer;
  font-weight: 500;
  font-size: 1rem;
  line-height: 1.15;
  letter-spacing: 0.025rem;
  border: none;
  border-radius: 0.25rem;
  border: 1px solid #aaa;
  background-color: transparent;
  color: #444;
  outline: none;
  text-decoration: none;
  user-select: none;
  width: auto;
  height: auto;
  margin: 0 0.5rem 0.75rem 0;
}
/* Hover and focus */
button:hover,
.button:hover,
input[type="submit"]:hover,
input[type="reset"]:hover,
input[type="button"]:hover,
button:focus,
.button:focus,
input[type="submit"]:focus,
input[type="reset"]:focus,
input[type="button"]:focus {
  text-decoration: none;
  border-color: #555;
  color: #000;
}
/* Extras */
.primary {
  color: #fff;
  border-color: #146eeb;
  background-color: #146eeb;
}
.primary:hover,
.primary:focus {
  color: #fff;
  border-color: #125ece;
  background-color: #125ece;
}
.secondary {
  border-color: #ebebeb;
  background-color: #ebebeb;
}
.secondary:hover,
.secondary:focus {
  border-color: #e0e0e0;
  background-color: #e0e0e0;
}
.round {
  border-radius: 1.25rem;
  padding: 0.5rem 1rem;
}
/* w/ an icon */
.icon-button {
  padding: 0.5rem 1rem 0.5rem 0.75rem;
  display: flex;
}
.icon-button .icon {
  width: 1.25rem;
  height: 1.25rem;
  margin-right: 0.25rem;
}
```

See [the button.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/button.css).

### Forms

This CSS assumes that you put your inputs inside your labels, like so:

```html
<label>
  Label for input
  <input type="text" />
</label>
```

It also assumes that you only ever really use inputs, textareas, checkboxes, and selects. (Personally, I don't find myself ever using any of the other form elements.)

```css
label {
  display: block;
  /* This value is a personal preference for spacing. */
  margin: 0.75rem 0;
}
input:not([type="checkbox"]),
textarea,
select {
  display: block;
  /* Change the height and size (padding) to match your aesthetic. */
  height: 2rem;
  padding: 0.25rem 0.5rem;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
  outline: none;
  width: 100%;
  margin: 0.25rem 0;
}
/* Also consider a hover state. It's less common but still cool. */
input:focus,
textarea:focus,
select:focus {
  /* This is my personal choice of blue as a base theme color. */
  border-color: #146eeb;
}
textarea {
  /* I prefer to not let people resize textareas. I never use that feature. */
  resize: none;
  height: auto;
  line-height: 1.15;
}
/* Checkboxes */
.checkbox-label {
  display: flex;
  /* Get the box vertically aligned with the label. */
  align-items: center;
}
input[type="checkbox"] {
  /* Add space between the box and the label */
  margin-right: 0.5rem;
}
```

See [the form.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/form.css).

### Search

This assumes you already use the form styles from above. And it assumes you build your search like so:

```html
<label class="search">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewBox="0 0 24 24"
    fill="none"
    stroke="currentColor"
    stroke-width="2"
    stroke-linecap="round"
    stroke-linejoin="round"
    class="search-icon"
  >
    <circle cx="11" cy="11" r="8" />
    <line x1="21" y1="21" x2="16.65" y2="16.65" />
  </svg>
  <input type="search" placeholder="Search" />
</label>
```

This demonstration really just shows how to put an icon prefix or postfix in an input. I usually use the stereotypical magnifying glass icon (from [Feather icons](https://feathericons.com/)) as a search input prefix. To get the icon positioned correctly, I absolutely position the icon inside the relatively positioned label. And since everything is inside the label, you can click right on the icon and it will still focus the input element.

"An icon says a ~~thousand~~ couple words."

```css
.search {
  position: relative;
}
.search-icon {
  position: absolute;
  top: 0;
  left: 0.125rem;
  width: 2rem;
  height: 2rem;
  padding: 0.375rem;
  margin: 0;
  line-height: 1;
  margin: 0;
  color: #777;
}
.search input[type="search"] {
  padding-left: 2rem;
}
```

See [the search.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/search.css).

### Cards

Google's _material design_ made these card things super popular, because they are the essence of "paper". (I'm not sure why that was such a big deal, but I gotta say I love material design.) Material Design calls for shadows to denote elevation, but I think we can keep things simple and not include any depth to the design.

"It's a screen. I'm not fooling anyone with 'box-shadows'."

Here's the basic HTML. (This assumes you've already included the button styles shown above.)

```html
<div class="card">
  <img class="card-media" src="https://via.placeholder.com/320x180" />
  <div class="card-content">
    <h5 class="card-title">Card title</h5>
    <p>
      Card text. Basic example of some text content inside a card. Wow, look at
      this great text.
    </p>
    <button class="card-action primary">Card action</button>
  </div>
</div>
```

Goes great with this hot cup of cascading styles.

```css
.card {
  /* This flex basis and max-width of 18rem is arbitrary. */
  flex: 1 0 18rem;
  max-width: 18rem;
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  /* This margin spacing is also arbitrary. */
  margin: 1rem 1rem 0 0;
}
.card-content {
  padding: 1rem;
}
.card-media {
  width: 100%;
}
.card-title {
  font-size: 1.125rem;
  font-weight: 500;
  line-height: 1.15;
}
.card-link {
  font-weight: 500;
  font-size: 1rem;
  padding: 0.125rem 0;
  margin: 0 1rem 0 0;
  letter-spacing: 0.025rem;
  display: inline-block;
}
.card-link:hover,
.card-link:focus {
  text-decoration: none;
  /* Darker blue */
  color: #125ece;
}
.card-action {
  margin: 0.25rem 1rem 0 0;
}
```

See [the card.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/card.css).

### Loaders / Spinners

AKA the loading indicator. Every app that makes web requests should use one of these things while awaiting a server response. I find that all my requests await responses over an indeterminate amount of time, so I can't use a progress indicator (like a progress bar). The best alternative is a little spinning wheel of some sort. It's the classic, iconic way of denoting "something is happening".

The simple spinning circle ones are my favorite. ("Simple is sexy.")

```html
<div class="loader"></div>
<div class="spinner"></div>
```

Both the loader and spinner are the same thing, but one has more blue than the other.

```css
.loader,
.spinner {
  /* Space to taste. */
  margin: 1rem;
  /* Resize to taste. */
  width: 4rem;
  height: 4rem;
  /* Color to taste. */
  border: 0.25rem solid #146eeb;
  border-top: 0.25rem solid #eee;
  border-radius: 50%;
  /* Speed the duration to taste. */
  animation: spin 1s linear infinite;
}
.loader {
  /* Swap colors: 3/4ths light gray and 1/4th blue */
  border: 0.25rem solid #eee;
  border-top: 0.25rem solid #146eeb;
}
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

See [the loader.css file](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/loader.css).

Now if you wanna get extra fancy, try out an animated GIF or SVG and just plop that on the screen via an `img` tag.

```html
<img src="./spinner.svg" class="fancy-loader" />
```

Then size it to whatever looks good.

```css
.fancy-loader {
  display: block;
  width: 6rem;
  height: 6rem;
  margin: 0 auto;
}
```

## But what about the grid system?

OH YEAH! Let's talk about layouts.

It's way easier than trying to create a bunch of containers and rows and lining up 12 column layouts... That's the stuff of the past.

These days, we can make life extremely simple with `F L E X B O X`.

I kinda get the impression that some developers think that flexbox is somehow scary and difficult and "high-level". But I think that's total nonsense. Flexbox is dead simple, easy to learn, easy to use, and just as understandable as any other bit of CSS you've ever learned.

(Here's a late night rant: I have some speculations on why flexbox is treated as "scary", and I think it might have to do with the older web dev folks who grew up without it and never took the time to learn the new CSS techniques introduced in 2009. They must've thought that that new, foreign stuff by the name of "flexbox" was some unholy work of sorcery. So whenever newer web devs would come to these elderly web devs for advice on it, the "senior" devs would shrug it off as "the new shiny things kids are chasing after these days", as if it were some fashion trend destined to be donated to thrift stores in the coming years. Or maybe they'd say to newer devs, "Oh come now, this is far too advanced for you to understand now. Only the greatest of minds can comprehend creating layouts with these advanced techniques." ... All of that is hogwash. And I don't ever use the word hogwash... Newer devs have zero background of previous layout techniques, so any and all layout techniques will be "new" and fresh to them no matter what. Teaching them to learn any layout technique will take all the same amount of effort on their part. But I'd argue that they'd learn faster with something a bit more "intuitive", like flexbox.)

### FLEXBOX

Let's break it down.

Flexbox is all about having a parent element with `display: flex;` that controls the layout of its immediate children elements, which have `flex: 0 1 auto;` by default.

```css
.flex-container {
  display: flex;
  flex-flow: row nowrap;
  /*
  flex-flow is the combination of flex-direction and flex-wrap.
    flex-direction: row;
    flex-wrap: nowrap;
  */
  justify-content: flex-start;
  align-items: stretch;
  align-content: flex-start;
}
.flex-item {
  flex: 0 1 auto;
}
```

See [the flexbox example page](https://davidhartsough.com/you-dont-need-bootstrap/flexbox.html) and [the source code](https://github.com/davidhartsough/you-dont-need-bootstrap/blob/master/flexbox.html).

Honestly, for the first few months while I was learning flexbox, I kept going back to this resource time and time again: [CSS Tricks' Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/). Highly recommend. 10/10 would look at again.

But! I want to convince you that the only CSS you need to learn is all written above ^^. For the flex container (the parent), you need to remember: `flex-flow`, `justify-content`, `align-items`, and (more rarely) `align-content`. (Of course, `display: flex;` as well.) Then for the flex item (the children), you just need to learn the `flex` property. Let's break these down.

#### `flex-flow`

The property `flex-flow` determines the direction of the _main_ axis as either `row` (default) or `column` and then whether or not to wrap the content with `nowrap` (default) or `wrap`.

```css
.flex-container {
  /* ... */
  flex-flow: row nowrap;
}
```

(Rarely will you use this, but it's worth mentioning that you can also do the `reverse` of any of these: `row-reverse`, `column-reverse`, and `wrap-reverse`.)

#### `justify-content`

The property `justify-content` determines the alignment and distribution of the flex items along the _main_ axis. If the flex container is a `row`, this property will function like the ole familiar word processor document justification options; by default, it will be left to right (`flex-start`), but you can set the content to be centered (`center`), right to left (`flex-end`), or some variation of what Word would consider "justified" (`space-between`, `space-around`, or `space-evenly`). BUT! Remember that it always is based on the direction of the _main_ axis. If you're using a `column`, then `flex-start` will be top to bottom, while `flex-end` will be bottom to top.

- flex-start (default): items are packed at the start of the flex-direction.
- flex-end: items are packed at the end of the flex-direction.
- center: items are packed in the center.
- space-between: items are evenly distributed with the first item at the start and the last item at the end.
- space-around: items are evenly distributed with equal space around them. All the items have equal "margin" on both sides.
- space-evenly: items are distributed so that the spacing between any two items _and_ the space to the edges is equal.

```css
.flex-container {
  /* ... */
  justify-content: flex-start;
}
```

#### `align-items`

The property `align-items` determines the spread of the items along the _cross_ axis. This means that if the flex container is a `row`, `align-items` will set the vertical spread of items (e.g. from top to bottom), whereas a `column` will use `align-items` to distribute the items horizontally (e.g. from left to right). It is a lot like `justify-content`, except it applies to the perpendicular (opposite) axis. Your primary options are:

- stretch (default): fill the container along the cross axis.
- flex-start: items are aligned at the start of the cross axis.
- flex-end: items are aligned at the end of the cross axis.
- center: items are centered in the cross axis
- baseline: items are aligned along their baselines (used more rarely)

```css
.flex-container {
  /* ... */
  align-items: stretch;
}
```

#### `flex`

Finally, the flex items (the children) can configure themselves with their own `flex` property. This property takes three values that determine whether or not the item can grow, whether or not the item can shrink, and what the base size should be (respectively). It is the shorthand combination of `flex-grow`, `flex-shrink`, and `flex-basis` (again, respectively). By default, a flex item will not grow (`0`), will shrink (`1`), and has an automatically determined size (`auto`). To toggle the grow and shrink properties, think of them like booleans: `0` means `false` or "don't do it", and `1` means `true` or "do it". Ex: `flex-grow: 1;` tells the item to grow to fill whatever space it can.

The third value, `flex-basis`, tells the item what size it should be when it's not trying to grow or shrink. If you want it to just follow along with your grow and shrink rules, just leave it be with `auto`. But if you want to get specific with sizes, set it to a pixel amount, a percentage, or any other unit of CSS measurement (like `rem`).

```css
.flex-item {
  flex: 0 1 auto;
  /* This is the shorthand for:
      flex-grow: 0;
      flex-shrink: 1;
      flex-basis: auto;
  */
}
```

### So what?

WELL! Lemme tell ya! This solves any and all layout problems you can imagine. But my personal favorite is that it can easily solve one of the most notorious problems in web dev styling: perfectly centering a child element inside a parent element both vertically and horizontally. Check this out. So simple!

```css
.flex-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## Boom bop!

That's it! Thank you, come again!
