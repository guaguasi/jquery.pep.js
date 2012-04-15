# pep.jquery.js

_put a little pep in your step_

=====

[DEMO](http://pep.briangonzalez.org)

Pep is a lightweight plugin for kinetic drag on mobile/desktop.

Pep was built out of a need for kinetic drag support for both mobile and desktop devices (click & drag). It uses the best of jQuery's animate functions along with CSS3 animations to bring full-blown kinetic drag that works on all HTML5-ready devices. 

Pep has built-in support for custom start, stop, and drag events, a debugger, and the ability to customize your own kinetic easing functions from <a href='http://matthewlein.com/ceaser/'>Matthew Lein's Ceaser</a>.


## How to use

Select your jQuery element, then pep it: `$('#peppable').pep()`. 

Alternatively, you can pass a hash of parameters. Below are the defaults.

### Parameters with their defaults:
            
            // show the debugger
            debug:                  false

            // CSS class to append to peppable object
            activeClass:            'active'

            // speed up drag (1 == unity, < 1 == slower, > 1 == faster)
            multiplier:             1,

            // manually fire a stop a peppable object when these events are fired (space delimited)
            stopEvents:             ""

            // get more easing functions here: http://matthewlein.com/ceaser/
            cssEaseString:          "cubic-bezier(0.210, 1, 0.220, 1.000)"

            // how long should it take to ease to its final resting place after mouseup/touchend 
            cssEaseDuration:        1000 

            // let peppable object move outside of window                                                  
            constrainToWindow:      false

            // bind peppable object to parent
            boundToParent:          false

            // fired...
            // ....while dragging
            drag:                   function(ev,obj){ /* fire on drag */ }

            // ... after stopping
            stop:                   function(ev,obj){ /* fire on stop */ }

            // ... after starting
            start:                  function(ev,obj){ /* fire on start */ }
            
So, for instance, you can log to the console while dragging, debug, and speed up the drag like so:
            
            var options = {
                debug:          true,
                drag:           function(ev,obj){ console.log('we're dragging!') },
                multiplier:     1.2
            };
            $('#peppable').pep(options);

Maybe you want to increase the ease time, change some text when you start dragging and upon ease completion:
            
              var options = {
                start:          function(ev,obj){ $('#title').text('Start!'); },
                drag:           function(ev,obj){ console.log('we're dragging!'); },
                rest:           function(ev,obj){ console.log('ease completed!'); }
            };
            $('#peppable').pep(options);

Other helper functions:
            
            obj.setMultiplier(val)          // programmatically increase or decrease the multiplier
            obj.enableEase()                // ... enable ease
            obj.disableEase()               // ... disable ease
            obj.forceStop()                 // ... force the object to stop

_Check out the demo over [here](http://pep.briangonzalez.org), and view the source for more tips 'n tricks._