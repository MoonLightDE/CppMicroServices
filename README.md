MLDE - C++ micro services library comunication
==============================================

MLDE OSGi-like C++ dynamic service registry for internals comunications, was forked from http://cppmicroservices.org

Moonlight related fork introduction:
------------------------------------

This library provides a dynamic service registry and module system integration for MLDE interaction between modules.

### Objetive library functionality:

It enables Moonlight Desktop developers to **modularize** and integrate using registers, external code 
into MLDE as embebed services. Umm this sounds like guindoze OS? well but currently its makes faster comunications  
of the QT5 implementation of MLDE, rather usage of dbus. Yeah its not standar but its light and faster.

Status
------

**STALED** patches and bugfixeds received, request for a mantainer.

Currenly the project library are staled  due MLDE implements light modified version of, if you are interesting 
to become mantainer please contact Azubieta or PICCORO for request and coordination in mail list of google group.

Requirements
------------

A C++ compiler with C++11 features its mandatory:

  - C++ compiler:
    - GCC >> 4.6
    - Clang >> 3.2
  - Cmake >> 2.9

Install and Supported Platforms
-------------------

At the moment of the last development artifact the library was staled in 2.X version, 
currently only Linux and some FreeBSD are supported.

### Build and install

The 'cmake' process are used to compile and install:

  1. Download source into a directory
  2. Prepare to compile: `mkdir build;cd build`
  3. Configure it: `cmake ..`
  4. Build: `make`

So once build and do a local unix like install: `make install`, and all files will be installed 
into the new `build/installed` directory due `PREFIX` are set to that path if not specified.

There's some variables that can be override at build:

+ `CMAKE_INSTALL_PREFIX` : by default set to `installed` under current build dir compilation
+ `LIBRARY_INSTALL_DIR` : by default set to `{PREFIX}/lib` here will be the shared libs files
+ `AUXILIARY_INSTALL_DIR` : by default set to `{PREFIX}/lib/cmake/{PROJECT_NAME}` and are the cmake files

There's some variables that can be set at install:

+ `DESTDIR` : by default set to `/` unless CMAKE_INSTALL_PREFIX were not set!

If you override one of, all the path will be changed.
Yeah when microcppservices started, those paths were set very bad!

If you wish this library documentation to be generated before install, you must have installed `doxygen`, 
the generated documentation will be at: `{PREFIX}/share/CppMicroServices/doc/`.

Legal
-----

Copyright (c) German Cancer Research Center. Licensed under the [Apache License v2.0][apache_license].

MLDE - C++ micro services Development implementation
==========================

ORIGIANL 3.X LIB: [![Build Status](https://secure.travis-ci.org/saschazelzer/CppMicroServices.png)](http://travis-ci.org/saschazelzer/CppMicroServices)

Essentially, the C++ Micro Services library provides you with a powerful dynamic service registry.
Each shared or static library has an associated `ModuleContext` object, through which the service
registry is accessed.

### integrating and registering service objects/applications

To query the registry for a service object implementing one or more specific interfaces, the code
would look like this:

```cpp
#include <usModuleContext.h>
#include <someInterface.h>

using namespace us;

void UseService(ModuleContext* context)
{
  ServiceReference serviceRef = context->GetServiceReference<SomeInterface>();
  if (serviceRef)
  {
    SomeInterface* service = context->GetService<SomeInterface>(serviceRef);
    if (service) { /* do something */ }
  }
}
```

### registering a service object:

Registering a service object against a certain interface looks like this:

```cpp
#include <usModuleContext.h>
#include <someInterface.h>

using namespace us;

void RegisterSomeService(ModuleContext* context, SomeInterface* service)
{
  context->RegisterService<SomeInterface>(service);
}
```

The OSGi service model additionally allows to annotate services with properties and using these
properties during service look-ups. It also allows to track the life-cycle of service objects.
Please see the [Documentation](http://cppmicroservices.org/doc_latest/index.html) for more
examples and tutorials and the API reference. There is also a blog post about
[OSGi Lite for C++](http://blog.cppmicroservices.org/2012/04/15/osgi-lite-for-c++).

