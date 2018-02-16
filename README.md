# Protocol Buffers - Usage and example code

This tutorial comes from [Protocol Buffers Website](https://developers.google.com/protocol-buffers/)

This directory contains example code that uses Protocol Buffers to manage an
address book. Two programs are provided for each supported language. The
add_person example adds a new person to an address book, prompting the user to
input the person's information. The list_people example lists people already in
the address book. The examples use the exact same format in all three languages,
so you can, for example, use add_person_java to create an address book and then
use list_people_python to read it.

These examples are part of the Protocol Buffers tutorial, located at:
  https://developers.google.com/protocol-buffers/docs/tutorials

## Running protobuf on remote.cs machines

We'll be using Protocol Buffers 3.5.1. It is already installed in my home
directory. This installation includes the protocol compiler (the protoc binary)
and the protobuf runtime for the 3 languages that we use - C++, Java and Python.

_Note: Please read the Protocol Buffers tutorial on above link to get better idea._

Similar to Apache Thrift, you need to specify environment variables at compile and runtime.
* Protobuf binary:
```bash
export PATH=/home/vchaska1/protobuf/bin:$PATH
```
The protocol compiler (protoc) binary is present at this location. It is required to
generate code from .proto files.

* Protobuf package configuration file:
```bash
export PKG_CONFIG_PATH=/home/vchaska1/protobuf/lib/pkgconfig
```


### C++

You can follow instructions in [../src/README.md](../src/README.md) to install
protoc and protobuf C++ runtime from source.

Then run "make cpp" in this examples directory to build the C++ example. It
will create two executables: add_person_cpp and list_people_cpp. These programs
simply take an address book file as their parameter. The add_person_cpp
programs will create the file if it doesn't already exist.

To run the examples:

    $ ./add_person_cpp addressbook.data
    $ ./list_people_cpp addressbook.data

Note that on some platforms you may have to edit the Makefile and remove
"-lpthread" from the linker commands (perhaps replacing it with something else).
We didn't do this automatically because we wanted to keep the example simple.

### Python

Follow instructions in [../README.md](../README.md) to install protoc and then
follow [../python/README.md](../python/README.md) to install protobuf python
runtime from source. You can also install python runtime using pip:

    $ pip install protobuf

Make sure the runtime version is the same as protoc binary, or it may not work.

After you have install both protoc and python runtime, run "make python" to
build two executables (shell scripts actually): add_person_python and
list_people_python. They work the same way as the C++ executables.

### Java

Follow instructions in [../README.md](../README.md) to install protoc and then
download protobuf Java runtime .jar file from maven:

    https://mvnrepository.com/artifact/com.google.protobuf/protobuf-java

Then run the following:

    $ export CLASSPATH=/path/to/protobuf-java-[version].jar
    $ make java

This will create the add_person_java/list_people_java executables (shell
scripts) and can be used to create/display an address book data file.

Observe that the C++, Python, and Java examples in this directory run in a
similar way and can view/modify files created by the Go example and vice
versa.
