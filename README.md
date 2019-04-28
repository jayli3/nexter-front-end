# [Nexter Real Estate - Front End](https://jayli3.github.io/nexter-front-end/ "nexter-front-end")
`Live:` https://jayli3.github.io/nexter-front-end/

A mockup real estate website. Front-end only.

## Features
- Fully responsive
- HTML and SASS only
- Emphasis on **CSS Grid**
- Uses **7-1 sass pattern** & **BEM** to create scalable and maintainable code.

###  Overview
----
The entire layout is done with a CSS Grid, making it very simple and straight forward to position the main containers as well as making the overall page responsive with very little media queries.

[![overview](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/ss01.png?raw=true "overview")](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/ss01.png?raw=true "overview")

##### Code for the entire layout:

```scss
.container{
	display: grid;
	grid-template-rows: 80vh min-content 40vw repeat(3, min-content);
	grid-template-columns: [sidebar-start] 6rem [sidebar-end full-start] minmax(6rem, 1fr) [center-start] repeat(8, [col-start] minmax(min-content, 14rem) [col-end]) [center-end] minmax(6rem, 1fr) [full-end];

	@include respond(II){
		grid-template-rows: 6rem 80vh min-content 40vw repeat(3, min-content);
		grid-template-columns: [full-start] minmax(6rem, 1fr) [center-start] repeat(8, [col-start] minmax(min-content, 14rem) [col-end]) [center-end] minmax(6rem, 1fr) [full-end];
	}

	@include respond(III){
		grid-template-rows: 6rem calc(100vh - 6rem) repeat(7, min-content);
	}
}
```

#### Responsiveness:
---
The website is fully responsive thanks to CSS Grids, and defining grid column widths arbitrarily:

```scss
grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
```
The `auto-fit` allows the grid items to fit into the grid dynamically.

[![responsiveness demo](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/gif01.gif?raw=true "responsiveness demo")](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/gif01.gif?raw=true "responsiveness demo")


#### CSS Grids:
---
Below is another example of using CSS Grid, this would have been very difficult to replicate without it.

[![css grid demo](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/ss02.png?raw=true "css grid demo")](https://github.com/jayli3/nexter-front-end/blob/master/README_resources/ss02.png?raw=true "css grid demo")





## NPM Dev Packages:
```json
"devDependencies": {
    "autoprefixer": "^9.5.1",
    "concat": "^1.0.3",
    "node-sass": "^4.11.0",
    "npm-run-all": "^4.1.5",
    "postcss-cli": "^6.1.2"
  }
```

## Handy NPM Scripts:
```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "watch-sass": "node-sass ./sass/main.scss ./css/style.css -w",
    "live-server": "live-server",
    "start": "npm-run-all --parallel watch-sass live-server",
    "compile-sass": "node-sass ./sass/main.scss ./css/style.comp.css",
    "concat-css": "concat -o ./css/style.concat.css ./css/style.comp.css ./css/icon-fonts.css",
    "prefix-css": "postcss --use autoprefixer -b 'last 10 versions' ./css/style.concat.css -o ./css/style.prefix.css",
    "compress-css": "node-sass ./css/style.prefix.css ./css/style.min.css --output-style compressed",
    "build-css": "npm-run-all compile-sass concat-css prefix-css compress-css"
  }
```