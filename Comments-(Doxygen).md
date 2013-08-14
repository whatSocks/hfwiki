The following document outlines how code should be commented in order for documentation to automatically be generated with Doxygen.

### Classes
Add a brief description to the class by using a C++ style comment with an additional slash.

    /// Handles input and output of audio for interface client
    class Audio : public QObject { 

That generates the following in Doxygen:

![class comment](http://f.cl.ly/items/2Q2a3R003c1g0e1F3R08/Screen%20Shot%202013-08-14%20at%201.19.17%20PM.png)

