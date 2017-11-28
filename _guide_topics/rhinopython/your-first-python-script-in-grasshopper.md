---
title: Your First Python Script in Grasshopper
description: This manual is for Grasshopper users who would like to create their own custom scripts using Grasshopper for Rhino.
authors: ['Scott Davidson']
author_contacts: ['scottd']
sdk: ['RhinoPython']
languages: ['Python']
platforms: ['Windows', 'Mac', 'Grasshopper']
categories: ['GhPython']
origin:
order: 1
keywords: ['python', 'commands', 'grasshopper']
layout: toc-guide-page
---

## Introduction

Scripting components works as an integrated part of GH. They can get input and produce output from and to other standard GH components. They can be used to create specialized functionality that opens up tremendous potential beyond the standard components.

But there is a cool twist… the GhPython component supports rhinoscriptsyntax functions. The rhinoscriptsyntax functions can be set to generate geometry inside of Grasshopper that does not live in the Rhino document. We are using a concept called “duck typing” to swap the document that the rhinoscriptsyntax functions target: from the Rhino document to a Grasshopper document. This means that the following script:

```python
import rhinoscriptsyntax as rs
for x in range(10):
    rs.AddPoint((x,0,0)
```

will add 10 points to the Rhino document when run from Rhino’s “_RunPythonScript” or “_EditPythonScript” commands. The same script will add 10 points to a Grasshopper document that can be passed on to other components when run inside a GhPython component.

Grasshopper supports multiple .NET scripting languages such as VB and C# to help develop custom code. There is also the Python component. Python supports multiple programming paradigms, often used as a scripting language, but is also used in a wide range of advanced programming contexts. The [Rhino.Python](http://developer.rhino3d.com/guides/rhinopython/) website directory is a great place to get more information about Python in Rhino in general.

![{{ site.baseurl }}/images/ghpython-component.png]({{ site.baseurl }}/images/ghpython-component.png){: .float-img-right width="275"}

The GhPython component brings:

- Rhinoscript syntax to Grasshopper
- a Python parallel to the C# and Vb.Net scripting components
- a dynamic UI with control over the number of inputs and outputs
- ability to reference .NET libraries and a huge number of Python packages
- integration with the Python editor included in Rhino



Rhino allows access to its algorithms through the Rhino SDK (software development kit). Rhino is written in C++ but it also provides a couple SDKs for scripting and programming languages.  The most basic SDK for Python is RhinoScriptSyntax. For more direct access to Rhino functions, more experienced programmers may choose to use the RhinoCommon SDK. There is extensive documentation about [RhinoScriptSyntax and Python](http://developer.rhino3d.com/guides/rhinopython/) on the Developer site. For more details about RhinoCommon, please refer to the [McNeel RhinoCommon Developer site](http://developer.rhino3d.com/guides/rhinocommon).

## Installing GhPython into Rhino

Only in Rhino for Windows, the Python component needs to the installed into Grasshopper.

1. Download [GhPython for Grasshopper from Food4Rhino](http://www.food4rhino.com/app/ghpython).
2. In Grasshopper, choose File > Special Folders > Components folder. Save the gha file there.
2. Right-click the file > Properties > make sure to "unblock" it.
3. Restart Rhino and Grasshopper.

A successful install will result in a Python component in the Math > Script toolbar:

![{{ site.baseurl }}/images/ghpython-installed.png]({{ site.baseurl }}/images/ghpython-installed.png){: .img-center width="95%"}


## Where to find the script components

To add the Python script component to the canvas, drag and drop the component from the “Script” panel under the “Maths” tab. The component first shows orange indicating a warning. This is because there is no code typed yet inside it. If you click on the bubble at the top-right corner, you can see what the warning is.

![{{ site.baseurl }}/images/ghpython-component.png]({{ site.baseurl }}/images/ghpython-component.png){: .img-center width="30%"}

The default script component has two inputs and two outputs. The user can change the names of input and output, the data type and data structure of the input and also add more inputs and outputs parameters or remove them.


![{{ site.baseurl }}/images/ghpython-component-detail.png]({{ site.baseurl }}/images/ghpython-component-detail.png){: .img-center width="95%"}

- x: first input of a .NET type (object).
- y: second input of a .NET type (object).
- out: output string with compiling messages and prints.
- A: Returned output of type object.


## The HelloWorld Script

Let's start with the classic ["Hello World!" example](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) for our first script.

1. Drag a Python component onto the Grasshopper canvas.
2. Add a Boolean component (Params toolbar) and connect it to the *x* input.
3. Add a Panel component and connect it to the *a* output.

![{{ site.baseurl }}/images/ghpython-helloworld-canvas.png]({{ site.baseurl }}/images/ghpython-helloworld-canvas.png){: .img-center width="75%"}

The "Hello World!" script will check for a *TRUE* in `x` to display the Hello World message through the 'a' output.

Double-click on the component to bring up the Python editor:

![{{ site.baseurl }}/images/ghpython-blankeditor.png]({{ site.baseurl }}/images/ghpython-blankeditor.png){: .img-center width="75%"}

Type in the following Python code:

```python
if x:
    a = "Hello World!"
```

Click on the OK button of the editor to get back to the Grasshopper Canvas.

If you toggle the Boolean switch from true to false, the Panel should display `Hello World!`.

![{{ site.baseurl }}/images/ghpython-helloworld.png]({{ site.baseurl }}/images/ghpython-helloworld.png){: .img-center width="75%"}

Congratulations!  You have compete your first Python script in Grasshopper.

To change the script, double-click o the Python component. Add another line of code:

```python
if x:
    a = "Hello World!"
else:
    a = "Nothing to say."
```

Now you can test that using the toggle.

---

## Related Topics

- [What is Python and RhinoScript?]({{ site.baseurl }}/guides/rhinopython/what-are-python-rhinoscript)
- [Loading Scripts]({{ site.baseurl }}/guides/rhinopython/python-loading-scripts)
- [Running Scripts]({{ site.baseurl }}/guides/rhinopython/python-running-scripts)
- [Canceling Scripts]({{ site.baseurl }}/guides/rhinopython/python-canceling-scripts)
- [Editing Scripts]({{ site.baseurl }}/guides/rhinopython/python-editing-scripts)
- [Scripting Options]({{ site.baseurl }}/guides/rhinopython/python-scripting-options)
- [Reinitializing Python]({{ site.baseurl }}/guides/rhinopython/python-scripting-reinitialize)
