# Introduction to Qt UI files

Qt is the leading cross-platform GUI development toolkit. This article will introduce you to Qt UI files. These files are XML documents, with the *.ui* file extension, which can be easily created/edited using Qt Designer, the WYSIWYG editor for Qt UI files. You can also launch Qt Designer directly from Qt Creator. Qt Creator automatically opens all the *.ui* files in the integrated Qt Designer, in Design mode.

**In this article wherever we use the word 'form', we mean the UI file.** 

##### Table of Contents
[1. Qt Designer](#qt-designer)  
[2. Creating your first form](#first-form)  
[3. Editing existing forms](#edit-form)  
[4. Further reading](#further-reading)

<a name="qt-designer">
## 1. Qt Designer
</a>

Qt Designer is the tool used to develop rich UIs with <a href="http://qt-project.org/doc/qt-5/qtwidgets-index.html" target="_blank">QtWidgets</a>

### 1.1 What can you do with Qt Designer?

1. Choose your form and objects
2. Lay the objects out on the form
3. Preview the form in different styles(or themes) (for instance, *Macintosh Style*, *Motif Style(Linux)*, *Windows Style* etc.)

Optionally, you can also connect the signals to the slots

<a name="first-form">
## 2. Creating your first form
</a>

###### Using Qt Creator? Follow these intructions before proceeding.
In Qt Creator, Goto **File** -> **New File or Project**. A dialog window appears. Below the '**Files and Classes**' title bar, click on the option '**Qt**'. Select '**Qt Designer Form**' from the right menu that appears. This should look something like this:

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/before-step1-using-qtcreator.png" width="400px">

Click on the '**Choose...**' button to proceed.

#### 2.1 Step 1 - Choosing a form

You start by choosing Widget from the New Form dialog.

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/step1.png" width="400px">

#### 2.2 Step 2 - Placing widgets on a form

After saving your form, you get to see something like this:

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/step2-1.png" width="400px">

On the left, you can see a list of all available widgets and layouts. On the right side, you have the information about the various widgets and/or layouts in our form. Below, you have the signal-slot editor (the one with the '+' and '-' icons).

Let us add some widgets to our form. This is very simple. Just drag any widget from the left widgets-list and drop it on the form. We will be placing a horizontal slider and a slider box in our form. The final result will look like this:

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/step2-2.png" width="400px">

#### 2.3 Step 3 - Connecting signal and slots

Click on the '+' icon. A new row gets added. Double click on '**&lt;sender&gt;**' to get a list of available options. Similarly, you can double click on '**&lt;signal&gt;**', '**&lt;receiver&gt;**' and '**&lt;slot&gt;**' to get a list of options for the respective action.

The ultimate result should look like this (look closely at the siganls and slots below the '+' and '-' icons and implement the same in your form):

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/step3.png" width="400px">

#### 2.4 Step 4 - Previewing our form

In Qt Creator, Goto **Tools** -> **Form Editor** -> **Preview...** to preview your form. Try to move the slider and you'll see the value of the spin box also changes. Change the value of the spin box and the slider corresponds to the set value. This 'magic' is done by Qt's awesome signal and slot method that we implemented in Step 3.

### Congratulations! You have created your very first Qt UI form successfully.

<a name="edit-form">
## 3. Editing existing forms
</a>

Editing existing forms is just as easy as creating them, just open the form in Qt Designer or Qt Creator. 

#### 3.1 Adding/Deleting widgets

To add widgets, you simply drag them from the left widgets-list and drop them in the form. To delete an existing widget, right-click on the widget and click on '**Delete**' option in the context menu that opens.

#### 3.2 Editing widget properties

When a widget is selected by clicking on it, you see a list of properties on your right side. Each widget has many properties, the most common being its '**objectName**' and '**geometry**'. To change any value of a property, click on it and enter your preferred value. This is portrayed in the following image:

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/editing-property-values-of-widgets.png" width="400px">

When you right-click on any widget, you get a context menu with many options like '**Send to Back**' and '**Bring to Front**'. These options are very helpful in further customising the look of your widget and form.

<img src="https://dl.dropboxusercontent.com/u/50262219/Intro-to-Qt-UI-files/right-click-context-menu-options.png" width="150px">

The above image shows a context menu which is shown when the user right-clicks on a '**QLabel**' widget. Similarly, you will find different options for every widget.

<a name="further-reading">
## 4. Further reading
</a>

1. Qt has its own manual on Qt Designer from ground zero <a href="http://qt-project.org/doc/qt-5/qtdesigner-manual.html" target="_blank">here</a>.
2. Read about layouts <a href="http://qt-project.org/doc/qt-5/layout.html" target="_blank">here</a>.

### References

1. http://qt-project.org/doc/qt-5/designer-to-know.html
2. http://qt-project.org/doc/qt-5/designer-quick-start.html
