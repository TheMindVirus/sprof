# sprof
Tool from glibc for tracing function calls inside shared libraries for Raspberry Pi OS

## Information
Patches have been made to remove `RT_CONSISTENT` assertions from `glibc/elf/dl-open.c` on lines 573 and 916 \
(actual line numbers may vary depending on commit) so that sprof stops complaining \
(glibc source: https://sourceware.org/git/glibc.git)

This repository also contains call traces of libbcm_host.so, libbrcmEGL.so and libbrcmGLESv2.so \
(optionally recompiled with `add_definitions("-g")` and `add_definitions("-pg")` to all files in \
`raspberrypi/userland/makefiles/cmake/toolchains/` but this is not absolutely necessary for traces)

## Traces
### These traces can be found here:
https://github.com/TheMindVirus/sprof/blob/main/trisprof-rel/prof_data/app.log
https://github.com/TheMindVirus/sprof/blob/main/trisprof-rel/prof_data/libbcm_host.so.p.log
https://github.com/TheMindVirus/sprof/blob/main/trisprof-rel/prof_data/libbrcmEGL.so.p.log
https://github.com/TheMindVirus/sprof/blob/main/trisprof-rel/prof_data/libbrcmGLESv2.so.p.log

## Links
### Here are some useful links to some of the sources of the libraries being traced:
https://github.com/raspberrypi/userland/blob/master/host_applications/linux/libs/bcm_host/bcm_host.c
https://github.com/raspberrypi/userland/blob/master/interface/khronos/egl/egl_client.c
https://github.com/raspberrypi/userland/blob/master/interface/khronos/glxx/glxx_client.c
https://github.com/raspberrypi/userland/blob/master/interface/khronos/common/khrn_client_rpc.h#L121

## Screenshot
![glcalls](https://github.com/TheMindVirus/sprof/blob/main/glcalls.png)
