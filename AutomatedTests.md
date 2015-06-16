

# BridJ's Automated Tests #

BridJ has grown big and there are many things to test.

If you [build BridJ from sources](Build.md), you can run a given test `MyTest` with `mvn test -Dtest=MyTest`.

## `PointerTest` and `TypedPointersTest` ##

These tests target `Pointer`, `PointerIO` and `CommonPointerIOs` classes.

`PointerTest` is generated out of a Velocity template that iterates on all BridJ primitives (java primitives + `CLong` + `SizeT` + `Pointer`) to make sure that all method variations in `Pointer` are covered.

TODO:
  * more tests with non-null byteOffset !
  * fix 3D arrays

## `StructTest` ##

Trivial test on simple structs.

TODO:
  * more tests !

## `ObjCTest` ##

Not functional !

## `MiscBugsTest` ##

Tests that specifically target some past or present bugs.

## `FunctionTest` ##

Trivial enum argument calls.

TODO:
  * more tests !

## `DemanglingTest` ##

Test GCC4 and VC9 C++ demanglers (given known mangled names, check we get back the expected signature).

TODO:
  * more tests, especially for VC9 !

## `CPPTest` ##

Basic C++ calls tests, including virtual vs. non-virtual calls, different calling conventions on supported platforms (stdcall...), destructor (including virtual destructor), static methods...

## `COMTest` ##

Windows-only test, just makes sure COM initializes well and that some known interface is instantiable.

TODO:
  * more tests !!!

## `ComparisonTest` ##

Compares performance of BridJ against JNA and Javolution :
  * Makes sure BridJ structs are one or two orders of magnitude faster that JNA structs for some operations (cast, creation...), and faster in all cases.
  * Compare calls of simple functions with JNA in direct and indirect modes and make sure BridJ is between 2-3x faster than JNA's direct mode and 20-30x faster than JNA's indirect mode.

## `CallbackTest` ##

Test basic Java to C and C to Java callbacks.

## `BridJTest` ##

Make sure BridJ is able to extract symbols from its native library

## `CallTest` ##

Template-generated test that has two parts : a native C++ file, compiled in libtest.so / test.dll / libtest.dylib, and a Java class that binds to the generated functions defined in the native test library.

Makes sure the generated functions return what we expect (result based on input arguments, varying their types thanks to the template).

# Test Coverage #

## Running Cobertura ##

It's easy to create a test coverage report by yourself if you [build BridJ from sources](Build.md) :
```
mvn cobertura:cobertura site
```
The coverage report is then in `target/site/cobertura`.

## Last published Cobertura reports ##

Every once in a while, we publish test coverage reports of the development version of BridJ.
If you want up-to-date reports, you should rather build BridJ from sources and look at the preceding section.

[BridJ's Latest Published Cobertura Report](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/)

Quick links within this report :

[Pointer](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.Pointer.html)
[PointerIO](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.PointerIO.html)
[CommonPointerIOs](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.CommonPointerIOs.html)
[BridJ](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.BridJ.html)
[CRuntime](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.CRuntime.html)
[CPPRuntime](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.cpp.CPPRuntime.html)
[MethodCallInfo](http://nativelibs4java.sourceforge.net/sites/nl4j-runtime-parent/bridj/cobertura/org.bridj.MethodCallInfo.html)