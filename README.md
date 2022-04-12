# ALP-RetroArch

How To Build RetroArch for ALP

- Source: https://github.com/libretro/RetroArch.git
- Build steps
```	
# clone source code
git clone https://github.com/libretro/RetroArch.git
cd RetroArch
 
# apply patch 
patch -p1 < RetroArch.patch

# build
source /opt/rk3399env.sh
export CFLAGS="-I$SDKTARGETSYSROOT/usr/include -DMESA_EGL_NO_X11_HEADERS"  # add include path 
PKG_CONF_PATH=$SDK_BASE/bin/pkg-config ./configure --disable-ffmpeg --disable-cg  --disable-pulse --disable-jack  --disable-x11 --enable-sdl2  --disable-opengl1 --disable-videocore --disable-v4l2 --disable-discord --enable-opengles3 --enable-opengles --enable-egl --disable-wayland --enable-opengles3 --enable-opengles3_1
 
make
```
- executable output:
	**retroarch** 
  
## Note:
  this patch binds to Core 4 and 5 for best performance on RK3399 SoC
