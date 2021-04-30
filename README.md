# sprof
Tool from glibc for tracing function calls inside shared libraries for Raspberry Pi OS

Patches have been made to remove `RT_CONSISTENT` assertions from `glibc/elf/dl-open.c` on lines 573 and 916 \
(actual line numbers may vary depending on commit) so that sprof stops complaining

This repository also contains call traces of libbcm_host.so, libbrcmEGL.so and libbrcmGLESv2.so \
(optionally recompiled with `add_definitions("-g")` and `add_definitions("-pg")` to all files in \
`raspberrypi/userland/makefiles/cmake/toolchains/` but this is not absolutely necessary for traces)

These traces can be found here:
