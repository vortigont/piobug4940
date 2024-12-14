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