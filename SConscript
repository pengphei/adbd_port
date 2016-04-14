#
# main building script
#

Import('genv')

adb_script = "adb/SConscript"
adb_files = genv.SConscript(adb_script)
genv.Install(genv["out"], adb_files)

cutils_script = "libcutils/SConscript"
cutils_files = genv.SConscript(cutils_script)
genv.Install(genv["out"], cutils_files)

