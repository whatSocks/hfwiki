The following document outlines how code should be commented in order for documentation to automatically be generated with Doxygen.

### Classes
Add a brief description to the class by using a C++ style comment with an additional slash.

    /// Handles input and output of audio for interface client
    class Audio : public QObject { 

That generates the following in Doxygen:

