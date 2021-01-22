# d3-v6-tip
A famous d3-tip lib adapted to the latest - d3.v6 version.

![](https://user-images.githubusercontent.com/6873202/92922793-6e621b00-f447-11ea-933d-50bac9a25fbb.gif)


## Foreword

d3.v6 introduced several changes and some of them concerns d3-tip.

Those are:

* Global d3.event has been removed
* Every event handler, from now on, will receive event as a first argument

d3-tip version which lies under this repository, is adapted to this change.

It also fixes one annoying bug, when several DOM tip instances were being created , which eventually would lead unexpected and undesirable results.

See [original documentation](https://github.com/caged/d3-tip/blob/master/docs/index.md), but please note changes in `tip.html` API.   
Short story is that, you will get same arguments in `tip.html()` as `tip.show()` receives, in the same order.

## Installing
If you are using npm

```npm i d3-v6-tip```

And then use it like this in your application
```javascript
import { tip as d3tip } from "d3-v6-tip";

const tip = d3tip()
```

Otherwise, you can load as a standalone library or as part of D3. ES modules, AMD, CommonJS, and vanilla environments are supported. In vanilla, a d3 global is exported:

If you want to load it as part of d3
```html
<script src="https://d3js.org/d3.v6.min.js"></script>
<script src="https://unpkg.com/d3-v6-tip@1.0.6/build/d3-v6-tip.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bumbeishvili/d3-tip-for-v6@4/d3-tip.min.css">

<script>

const tip = d3.tip()

</script>
```

If you want to load it as standalone
```html
<script src="https://d3js.org/d3-selection.v2.min.js"></script>
<script src="https://unpkg.com/d3-v6-tip@1.0.6/build/d3-v6-tip.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bumbeishvili/d3-tip-for-v6@4/d3-tip.min.css">

<script>
var svg = d3.select('svg');

/* Initialize tooltip */
var tip = d3.tip().attr('class', 'd3-tip').html((EVENT,d)=> d );

    
/* Invoke the tip in the context of your visualization */
svg.call(tip)

    
// -------------- Simplest usage ----------------
svg.selectAll('rect')
    .on('mouseover', tip.show)
    .on('mouseout', tip.hide)
        
    
// ------------- Conditional usage -------------
svg.selectAll('rect')
    .on('mouseover', (event,d)=>{
          if(someCondition) tip.show(event,d);
     })
    .on('mouseout', tip.hide)
    
    
// ------------- Showing tip on particular element, but based on other DOM element's data -------------
svg.selectAll('g')
    .on('mouseover', function(event,d) {
          const element = d3.select(this)
                            .select('.particular-element');
          tip.show(event, d, element.node())
     })
    .on('mouseout', tip.hide)
</script>
```


See   [minimal jsfiddle example here](https://jsfiddle.net/aftjeb0g/2/)




## Style
for default styling, include this [css file](https://github.com/bumbeishvili/d3-v6-tip/blob/master/src/d3-tip.css) into your app
```css
.d3-tip {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  padding: 20px;
  pointer-events: none !important;
  color: #203d5d;
  box-shadow: 0 4px 20px 4px rgba(0, 20, 60, .1), 0 4px 80px -8px rgba(0, 20, 60, .2);
  background-color: #fff;
  border-radius: 4px;
}

/* Creates a small triangle extender for the tooltip */
.d3-tip:after {
  box-sizing: border-box;
  display: inline;
  font-size: 10px;
  width: 100%;
  line-height: 1;
  color: #fff;
  position: absolute;
  pointer-events: none;
}

/* Northward tooltips */
.d3-tip.n:after {
  content: "▼";
  margin: -1px 0 0 0;
  top: 100%;
  left: 0;
  text-align: center;
}

/* Eastward tooltips */
.d3-tip.e:after {
  content: "◀";
  margin: -4px 0 0 0;
  top: 50%;
  left: -8px;
}

/* Southward tooltips */
.d3-tip.s:after {
  content: "▲";
  margin: 0 0 1px 0;
  top: -8px;
  left: 0;
  text-align: center;
}

/* Westward tooltips */
.d3-tip.w:after {
  content: "▶";
  margin: -4px 0 0 -1px;
  top: 50%;
  left: 100%;
}
```


## History

* [Caged](https://github.com/caged/d3-tip) created d3-tip for d3.v3
* [cgav](https://github.com/cgav/d3-tip) converted it to d3-v4 and ES6 code
* [VACLAB](https://github.com/VACLab/d3-tip) removed ES6 specific code for wider browser support
* [bumbeishvili](https://github.com/bumbeishvili/d3-tip-v6) adapted for newer d3.v6 version and [published to NPM](https://www.npmjs.com/package/d3-v6-tip)


## Repo Author
 [David   B (twitter)](https://twitter.com/dbumbeishvili)  
 [David   B (linkedin)](https://www.linkedin.com/in/bumbeishvili/)  

I am available for freelance data visualization work. Please [contact me](https://davidb.dev/contact) in case you'd like me to help you with my experience and expertise
