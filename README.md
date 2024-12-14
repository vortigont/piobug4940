dummy project to demonstrate Platformio bug [4940](https://github.com/platformio/platformio-core/issues/4940) that does not builds with default core and builds fine with [4941](https://github.com/platformio/platformio-core/pull/4941/files)

The dependency there is like this:
```
PROJECT
  | -- EmbUI (lib from a registry)
           | -- esp32-flashz (lib from a registry)
           |      | -- Update (bundled lib from Arduino core )
           |      | -- Ticker (bundled lib from Arduino core )
           | -- other 3rd party libs
```

Build errors:
```
In file included from .pio/libdeps/test/esp32-flashz/src/flashz.cpp:30:
.pio/libdeps/test/esp32-flashz/src/flashz.hpp:40:10: fatal error: Update.h: No such file or directory

****************************************************************
* Looking for Update.h dependency? Check our library registry!
*
* CLI  > platformio lib search "header:Update.h"
* Web  > https://registry.platformio.org/search?q=header:Update.h
*
****************************************************************

 #include <Update.h>
          ^~~~~~~~~~
compilation terminated.                                                                                                                                       
Compiling .pio/build/test/libbfc/AsyncUDP/AsyncUDP.cpp.o                                                                                                      
*** [.pio/build/test/libc51/esp32-flashz/flashz.cpp.o] Error 1                                                                                                
In file included from .pio/libdeps/test/esp32-flashz/src/flashz-http.cpp:30:                                                                                  
.pio/libdeps/test/esp32-flashz/src/flashz-http.hpp:39:10: fatal error: Ticker.h: No such file or directory         
```
