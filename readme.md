# Native Mac OS X Oculus Rift

a very simple OpenGL project with the Oculus SDK already integrated

![ScreenShot](https://raw.github.com/robbykraft/SimpleOculus/master/SimpleOculus/screenShot.jpg)

# features

* barrel warp shader
* keyboard:
`F` full screen `+` `-` change virtual interpupillary distance `△` `▽` `◁` `▷` walk around
* mouse: click to activate mouse look 

__some help is still needed with:__

* L&R eye orientation
* interpupillary distance

------

## Xcode + LibOVR integration instructions

**NOTE THIS IS ALREADY DONE. you don’t have to do any of this**, these are notes for how I built this project from scratch- in case you want to do it yourself.

------

> ### from a blank OSX Cocoa project

> Drag LibOVR into Xcode Project, uncheck all “Add to Target”

>  

> Link libovr.a (drag it from LibOVR/Lib/MacOS/Debug), and IOKit

> ![Libraries](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/Libraries.png)

>  

> Set architecture to 64-bit Intel (x86_64)

> ![Architectures](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/Architectures.png)

>  

> C++ settings- set the standard library to libstdc++ (GNU C++ standard library), disable exceptions, disable runtime types

> ![LLVM](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/LLVMLanguage.png)

>  

> Coordinate your Search Paths to wherever the LibOVR folder resides:
> Header Search Paths (same for debug and release): LibOVR/Src, LibOVR/Include
> Library Search Paths:
> - Debug : LibOVR/Lib/MacOS/Debug
> - Release : LibOVR/Lib/MacOS/Release

> ![SearchPath](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/SearchPathsHeader.png)

> ![SearchPath](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/SearchPathsLibrary.png)

> Any classes which include OVR.h, and the classes which include THOSE classes, must be named *.mm, or must be marked as Objective-C++ source. Leave the .h files alone.

> ![sample](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/Objective-C++.png)

> ------

> For reference: this is the example’s directory structure

> ![Finder](https://raw.github.com/robbykraft/SimpleOculus/master/tutorial/Finder.png)

> ------

> ### Test it

> edit `main.mm`:

```
#import <Cocoa/Cocoa.h>
#include "OVR.h”

using namespace OVR;

int main(int argc, const char * argv[])
{
    System::Init();
    return NSApplicationMain(argc, argv);
}
```

> If this builds, success!