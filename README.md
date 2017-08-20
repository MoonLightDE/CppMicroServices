MLDE - C++ micro services library comunication
==============================================

MLDE OSGi-like C++ dynamic service registry for internals comunications, was forked from http://cppmicroservices.org

Moonlight related fork introduction:
------------------------------------

This library provides a dynamic service registry and module system integration.

### Objetive library functionality:

It enables Moonlight Desktop developers to **modularize** and integrate using registers, external code into MLDE as embebed services. Umm this sounds like guindoze OS? well but currently its faster due the QT5 impelmentation of MLDE.

Status
------

**STALED** patches and bugfixeds received, request for a mantainer.

Currenly the project library are staled  due MLDE impelments light modified version of, if you are interesting to become mantainer please contact Azubieta or PICCORO for request and coordination in issue mlde.d.moonlightde#39.

Requirements
------------

A C++ compiler with C++11 features its mandatory:

  - C++ compiler:
    - GCC >> 4.6
    - Clang >> 3.2
  - Cmake >> 2.9

Install and Supported Platforms
-------------------

Extended documentation can be foun in docs directory of the MLDE main repository. At the moment of the last development artifact the library was staled in 2.X version, currently only Linux and some FreeBSD are supported.

### Build and install

The 'cmake' process are used to compile and install:

  1. Download source into it to compile: `mkdir build;cd build`
  2. Configure it: `cmake .. -DLIBRARY_INSTALL_DIR=/usr/local/lib`
  3. Build: `make`

So once build and do a local unix like install: `make install`, if you wish this library documentation to be generated before install, you must have installed `doxygen`, the generated documentation will be at: `/usr/local/share/CppMicroServices/doc/`.

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

