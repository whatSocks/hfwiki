The following document outlines how code should be commented in order for documentation to automatically be generated with Doxygen.

### Classes
Add a brief description to the class by using a C++ style comment with an additional slash.

    /// Handles input and output of audio for interface client
    class Audio : public QObject { 

That generates the following in Doxygen:

![class comment](http://f.cl.ly/items/3A0z1h0W3I2c3d2x1F3p/Screen%20Shot%202013-08-14%20at%201.20.27%20PM.png)

### Methods
Add appropriate comments to a method using the following comment style.

    /// Processes a received audio packet
    /// \param unsigned char* receivedData the received packet
    /// \param int receivedBytes the number of bytes received
    /// \return int number of samples processed
    /// \thread network receive
    int addReceivedAudioToBuffer(unsigned char* receivedData, int receivedBytes);

The first line in the comment is a brief description of the method.
Parameters to the method begin with `\param`, then the type of the parameter, the name of the parameter, and a brief description of the parameter.
The method return begins with `\return`, then the type of the return and a brief description
The `\thread` tag is an optional custom tag to designate which thread the method must be called on (if not the main thread).

That generates the following in Doxygen:

![method comments](http://f.cl.ly/items/1T273V1r0C2c2E1Z2P0c/Screen%20Shot%202013-08-14%20at%201.22.50%20PM.png)