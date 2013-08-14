The following document outlines how code should be commented in order for documentation to automatically be generated with Doxygen.

### Classes
Add a brief description to the class by using a C++ style comment with an additional slash.

    /// Handles input and output of audio for interface client
    class Audio : public QObject { 

That generates the following in Doxygen:

![class comment](http://f.cl.ly/items/3A0z1h0W3I2c3d2x1F3p/Screen%20Shot%202013-08-14%20at%201.20.27%20PM.png)
