# d3-tip-v6
Famous d3-tip version fitted to the latest - d3.v6 


## Foreword

d3.v6 introduced several changes and some of them concerns d3-tip.

Those are:

* Global d3.event has been removed
* Every event handler, from now on, will receive event as a first argument


## common usage of d3-tip-for-v6.


```javascript
svg = d3.select('svg');

/* Initialize tooltip */
var tip = d3.tip().attr('class', 'd3-tip').html(d=> d; );

/* Invoke the tip in the context of your visualization */
svg.call(tip)



// -------------- Simplest usage ----------------

svg.selectAll('rect')
    .on('mouseover', tip.show)
    .on('mouseout', tip.hide)
    
    
    
// ------------- Conditional usage -------------

svg.selectAll('rect')
    .on('mouseover', (event,d)=>{
          if(someCondition) tip.show(event);
     })
    .on('mouseout', tip.hide)
    
    

// ------------- Showing tip on particular element, but based on other DOM element's data -------------

svg.selectAll('g')
    .on('mouseover', function(event,d) {
          const element = d3.select(this)
                            .select('.particular-element');
          tip.show(d, element.node())
     })
    .on('mouseout', tip.hide)
    
```


## History

* [Caged](https://github.com/caged/d3-tip) created d3-tip for d3.v3
* [cgav](https://github.com/cgav) converted it to d3-v4 and ES6 code
* [VACLAB](https://github.com/VACLab/d3-tip) removed ES6 specific code for wider browser support
* [bumbeishvili](https://github.com/bumbeishvili/d3-tip-v6) adapted for newer d3.v6 version
