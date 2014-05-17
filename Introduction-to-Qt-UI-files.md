# Introduction to Qt UI files

Qt is the leading cross-platform GUI development toolkit. This article will introduce you to Qt UI files. These files are XML documents, with the *.ui* file extension, which can be easily created/edited using Qt Designer, the WYSIWYG editor for Qt UI files. You can also launch Qt Designer directly from Qt Creator. Qt Creator automatically opens all the *.ui* files in the integrated Qt Designer, in Design mode.

**In this article wherever we use the word 'form', we mean the UI file.** 

#### Table of Contents
1. [Qt Designer](#qt-designer)  
2. [Creating your first form](#first-form)  
3. [Editing existing forms](#edit-form)
4. [Qt UI files and C++](#ui-cpp)  
5. [Further reading](#further-reading)

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

<a name="ui-cpp">
## 4. Qt UI files and C++
</a>

**Note: This section of the article is largely based on the official Qt document which can be accessed <a href="http://qt-project.org/doc/qt-5/designer-using-a-ui-file.html" target="_blank">here</a>. We recommend you to go through it for an all-round concept of using UI files in your Qt app.**

At compile time, forms are converted to C++ code in the form of a C++ header file. These header files can be easily used in our C++ classes to interact with the form and implement the logic behind all the widgets of the form.

**Naming scheme of the header files:**

Suppose we have a form named '**myform.ui**' which we have created using Qt Designer or Qt Creator. The header file for this form will then be '**ui_myform.h**'. For your knowledge, the program that converts *.ui* files into header files is called '**uic**' Read more about '**uic**' <a href="http://qt-project.org/doc/qt-5/uic.html" target="_blank">here</a>.

### 4.1 The Direct Approach

To use the direct approach, we include the ui_myform.h file directly in main.cpp:

```cpp
#include "ui_myform.h"
```

The main function creates the form widgets by constructing a standard QWidget that we use to host the user interface described by the myform.ui file.

```cpp
#include <QApplication>
#include <QWidget>

#include "ui_myform.h"

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    QWidget *widget = new QWidget;
    Ui::MyForm ui;
    ui.setupUi(widget);
    widget->show();
    return app.exec();
}
```

In this case, the Ui::MyForm is an interface description object from the ui_myform.h file that sets up all the dialog's widgets and the connections between its signals and slots.

### 4.2 The Single Inheritance Approach (Preferred)

The direct approach provides a quick and easy way to use simple, self-contained components in your applications. However, components created with Qt Designer often require close integration with the rest of the application code.

In this approach, we subclass a Qt widget and set up the user interface from within the constructor. Components used in this way expose the widgets and layouts used in the form to the Qt widget subclass, and provide a standard system for making signal and slot connections between the user interface and other objects in your application. The generated Ui::MyForm structure is a member of the class.

The subclass is defined in the following way:

```cpp
class MyForm : public QWidget
{
    Q_OBJECT

public:
    MyForm(QWidget *parent = 0);

private slots:
    void slotOne();
    void slotTwo();

private:
    Ui::MyForm ui;
};
```

The important feature of the class is the private ui object which provides the code for setting up and managing the user interface.

The constructor for the subclass constructs and configures all the widgets and layouts for the dialog just by calling the ui object's setupUi() function. Once this has been done, it is possible to modify the user interface as needed.

```cpp
MyForm::MyForm(QWidget *parent)
    : QWidget(parent)
{
    ui.setupUi(this);
}
```

**Advantages:**

The advantages of this approach are its simple use of inheritance to provide a QWidget-based interface, and its encapsulation of the user interface widget variables within the ui data member. We can use this method to define a number of user interfaces within the same widget, each of which is contained within its own namespace, and overlay (or compose) them. This approach can be used to create individual tabs from existing forms, for example.

**Alternative method (preferred for large applications):**

Alternatively, the Ui::MyForm structure can be made a pointer member of the class. The header then looks as follows:

```cpp
namespace Ui {
    class MyForm;
}

class MyForm : public QWidget
...
virtual ~MyForm();
...
private:
    Ui::MyForm *ui;
...
```

The corresponding source file looks as follows:

```cpp
#include "ui_myform.h"

MyForm::MyForm(QWidget *parent) :
    QWidget(parent), ui(new Ui::MyForm)
{
    ui->setupUi(this);
}

MyForm::~MyForm()
{
    delete ui;
}
```

The advantage of this approach is that the user interface object can be forward-declared, which means that we do not have to include the generated ui_myform.h file in the header. The form can then be changed without recompiling the dependent source files. This is particularly important if the class is subject to binary compatibility restrictions. We generally recommend this approach for libraries and large applications.

<a name="further-reading">
## 5. Further reading
</a>

1. Qt has its own manual on Qt Designer from ground zero <a href="http://qt-project.org/doc/qt-5/qtdesigner-manual.html" target="_blank">here</a>.
2. Read about layouts <a href="http://qt-project.org/doc/qt-5/layout.html" target="_blank">here</a>.

### References

1. http://qt-project.org/doc/qt-5/designer-to-know.html
2. http://qt-project.org/doc/qt-5/designer-quick-start.html
3. http://qt-project.org/doc/qt-5/designer-using-a-ui-file.html