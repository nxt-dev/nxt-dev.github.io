## Introduction

The primary function of nxt is to visualize and automate programming tasks 
related to computer graphics and linear processing. The intent is to bridge 
the gap between one-off scripting and general purpose tools through the use of 
inheritance, layering, and string tokens.
## Why use nxt?
The core functionality of nxt was built with insights from industry veterans 
of various technical and artistic backgrounds. We set out to bring to the
 table a simple set of principles:

- Visualize a map of what a complex script is actually doing. 
[Nodes](reference.md#node), [inheritance](concepts.md#inheritance), and
connection lines are easy to understand. However, we've gone a step further 
and added string [tokens](reference.md#tokens). An instant visualization 
of what an attribute value _actually_ is. Our tokens can be used _almost_
anywhere inside nxt and are dynamically "resolved" during execution. Allowing the
user to see exactly what data is flowing around without the use of an
external debugger.
- Encourage collaboration though [layering](reference.md#layers) and multi context graphs. 
With our layering system it is easy for departments to share base workflows and
utility nodes. Since layering is non-destructive graphs can referenced built on 
without worrying about breaking someone else's graph. With [multi context](extensions.md#creating-custom-contexts) 
graphs a Maya user, for example, can directly call a Houdini graph from inside Maya. 
Alternatively, graphs can call other graphs in the same context, allowing 
interdependent graphs to be developed simultaneously.
- Make code accessible to everyone. Artists can modify attributes like their
used to and learn to make simple code changes that normally would require a 
TD to intervene. We're not visual programming, but rather a friendly visual
portal into code.

## What does nxt do?
In the simplest of terms nxt combines multiple layers of nodes into a single 
composite layer that is then executable. Something like Photoshop layers for
your code, you're able to mute, solo, override, and extend layers of code. 
The resulting composite of the code clearly visualizes where attributes and
their values came from. Colors, node paths, and conveniently placed buttons/links 
allow users to quickly jump to and correct erroneous values.

*Example character rig with a general to specific layer structure*
![layers](images/nxt_layers01.gif)

## Limitations
- We currently do not support asynchronous execution in a single graph. Our 
current focus is on lineal scripts.
- We are [not visual programming](reference.md#design-philosophy), no for loop nodes sorry.
- We currently experimentally support Python 3, it is possible to lose layout and break point preferences 
by switching back and forth between Py2/3.

---

<div style="text-align: center;">
<h4>Special Thanks</h4>
</div>

!!! Note "Sunrise Productions"
    We would like to thank [Sunrise Productions](https://sunriseproductions.tv/) for providing us a studio incubator for 2019 and 2020. 
    Sunrise kept food on the table and believed in nxt before it was fully realized. Without their support we would never have made it this far.

!!! Note "SVAD Productions"
    We would like to thank the [School of Visual Art and Design](https://www.southern.edu/visualartanddesign/) NXT began in 2017 as a research project at SVAD. 
    Originally with the goal to make it the core rigging framework, nxt quickly grew into the backbone of pipeline.
    We are grateful for SVAD providing the resources, education, and sponsorship to get us started.


<table style="text-align: center">
<tr>
<th>Walt Yoder</th>
<th>mGear (Miquel Campos)</th>
</tr>
<tr>
<th>Matt Schiller</th>
<th></th>
</tr>
</table>

---

<div style="text-align: center;">
<h1>The nxt contributors</h1>
</div>

<table style="text-align: left;">
<tr>
<th><a href="https://imlucasbrown.com" target="_blank"><img src="../images/lucas_bw.png" style="width:100px;" alt="Lucas"/> <b>Lucas Brown</b> - Developer</a></th>
<th><a href="https://michael.aldrich.online/" target="_blank"><img src="../images/michael_bw.png" style="width:100px;" alt="Michael"/> <b>Michael Aldrich</b> - Developer</a></th>
</tr>
<tr>
<th><a href="https://www.linkedin.com/in/aaroneadams/" target="_blank"><img src="../images/aaron_bw.png" style="width:100px;" alt="Aaron"/> <b>Aaron Adams</b> - Visionary & Founder</a></th>
<th><img src="../images/zach_bw.png" style="width:100px;" alt="Zach"/> <b>Zach Gray</b> - Contributor</th>
</tr>
</table>