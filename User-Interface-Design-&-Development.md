This document should function as an ever evolving resource around both design philosophy as it relates to UI, and development tips for our distributed UI development team.

## General thinking around UI
We should do everything in our power to reduce stress while using High Fidelity. This should inform color decisions (neutral colors, low contrast -- we probably want to use less black on something like the Import Dialog as it's currently implemented), behavioral decisions when implementing animations, transitions and effects (nothing too abrupt; aim for elegance and subtlety).

Where a vibrant orange is used for the Alpha branding as a subtle warning: this product isn't perfect; it will break. Inside our app, we should aim for a sense of security, peace and honesty.

The behaviour of windows should create feeling of togetherness between each window. A common paradigm in 3D apps is to show a 3D window, and the 2D dialogs atop, where necessary. We should challenge this, seeking out a solution that create a connection between 2D and 3D elements, rather than a hard separation.

We are in an experimental phase. There are many challenges we face with trying to combine both 2D and 3D elements in the same view and make the experience pleasant. I'm not sure when we'll arrive at the place we're looking to go, or exactly what it looks like. For now, we're using Qt because it's accessible and a good tool for prototyping, but in the future we may decide that UI should all be built in JavaScript and function more like the web/HTML/CSS than Qt does. And beyond that we might get to a place where we decide there's no place for anything truly 2D – everything might be in world; your avatar might just pull out a tablet, and you'll change settings on that tablet screen ... full immersion.

The approach we are exploring now involves 'docked' windows overlayed atop the 3D window. These windows are design to avoid too much obstruction of the 3D view by appearing on the side, and maintain a feeling of unity between the window and the 3D view because of their 'docked' nature. Because the window is not obstrusive, it should also feel less obtrusive to open and close them frequently, making functionality like checking which scripts are currently running highly accessible.

![](http://un.titled.name/ULBh/hifi-interface-v34-running-scripts2.png)

In a few attempts at implementing these 'docked' windows, I've seen an approach where the main window is simply split into 2 sections; the 3D window is resized, changing the aspect ratio and giving a jarring 'something weird just happened; my viewable area just got squished!' experience, while the other section reveals the 2D UI. Whereas the overlay approach simply places one element (window) on top of another (window), an experience humans are used to (you have a book open with a beautiful picture and then place a piece of paper on top of it). Where do we see our view 'squished' from either side in the real world? -- We are simply not comfortable with that.

## Qt related findings

1. Paraphrasing @ddobrev:
Docked windows are not supposed to appear outside their parent window  ​(though @Chris7 told me there was no problem on Linux​)​​;the Qt people have promised to fix it for Qt 5.2.2.