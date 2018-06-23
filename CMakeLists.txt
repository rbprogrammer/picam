cmake_minimum_required(VERSION 3.7)
project(picam)

set(CMAKE_CXX_STANDARD 11)


# FIXME these contains shell commands!
set(CFLAGS "-DSTANDALONE -D__STDC_CONSTANT_MACROS -D__STDC_LIMIT_MACROS -DTARGET_POSIX -D_LINUX -fPIC -DPIC -D_REENTRANT -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -U_FORTIFY_SOURCE -Wall -g -DHAVE_LIBOPENMAX=2 -DOMX -DOMX_SKIP64BIT -ftree-vectorize -DUSE_EXTERNAL_OMX -DHAVE_LIBBCM_HOST -DUSE_EXTERNAL_LIBBCM_HOST -DUSE_VCHIQ_ARM -Wno-psabi -I/opt/vc/include/ -I/opt/vc/include/interface/vcos/pthreads -I/opt/vc/include/interface/vmcs_host/linux -I/opt/vc/src/hello_pi/libs/ilclient `freetype-config --cflags` `pkg-config --cflags harfbuzz fontconfig libavformat libavcodec` -I/usr/include/fontconfig -g -Wno-deprecated-declarations -O3")
set(LDFLAGS "-g -Wl,--whole-archive -lilclient -L/opt/vc/lib/ -L/usr/local/lib -lbrcmGLESv2 -lbrcmEGL -lopenmaxil -lbcm_host -lvcos -lvchiq_arm -lpthread -lrt -L/opt/vc/src/hello_pi/libs/ilclient -Wl,--no-whole-archive -rdynamic -lm -lcrypto -lasound `freetype-config --libs` `pkg-config --libs harfbuzz fontconfig libavformat libavcodec`")

FILE(GLOB PICAM_HEADERS *.h)
FILE(GLOB PICAM_SOURCES *.c)

add_executable(picam ${PICAM_HEADERS} ${PICAM_SOURCES})
