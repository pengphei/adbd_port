#
# building struct
#

import os

platform = ARGUMENTS.get('platform','x64')  

EXE_PATH = ''
PREFIX = ''
STAGING_DIR = ''

if "mipsel" == platform:
    EXE_PATH = '../openwrt/staging_dir/toolchain-mipsel_24kec+dsp_gcc-4.8-linaro_uClibc-0.9.33.2/bin/'
    PREFIX = EXE_PATH+ '/mipsel-openwrt-linux-uclibc-'
    STAGING_DIR = '../openwrt/staging_dir/target-mipsel_24kec+dsp_uClibc-0.9.33.2/'
elif "arm" == platform:
    EXE_PATH = "../../globot/buildroot/output/host/usr/bin/"
    PREFIX = EXE_PATH+ "arm-linux-gnueabihf-"
    STAGING_DIR = os.path.abspath(".") + "/../../globot/buildroot/output/staging/"
    #EXE_PATH = '~/build/gcc-linaro/bin/'
    #PREFIX = EXE_PATH+ '/arm-linux-gnueabihf-'
elif "x86" == platform:
    STAGING_DIR = "/"
elif "x64" == platform:
    STAGING_DIR = "/"

genv = Environment()

genv["out"] = "#build/out/"+platform
genv["build"] = "#build/var/"+platform
genv["platform"] = platform
genv["LIBPATH"] = genv["out"]
    
genv["CC"] = PREFIX + 'gcc'
genv["CXX"] = PREFIX + 'g++'
genv["AS"] = PREFIX + 'gcc'
genv["AR"] = PREFIX + 'ar'
genv["LINK"] = PREFIX + 'gcc'
genv["OBJCOPY"] = PREFIX + 'objcopy'
genv["NM"] = PREFIX + 'nm'
genv["ENV"] = os.environ
genv["ENV"]["STAGING_DIR"] = STAGING_DIR
genv["STAGING_DIR"] = STAGING_DIR

genv.PrependENVPath ('PATH', EXE_PATH)

Export("genv")

script = 'SConscript'
genv.SConscript(script, variant_dir=genv["build"])
