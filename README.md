## Download the Source Code

android 10.0:
```
mkdir -p <WORKING_DIRECTORY>
cd <WORKING_DIRECTORY>

repo init -u https://github.com/khadas/android_manifest.git -b khadas-edge-Qt
repo sync -j4

// create development branches
repo start <BRANCH_NAME> --all
```

## Build images
### Compiling u-boot
```
cd <project-name>
make mrproper
./make.sh kedge
```

### Compiling kernel：
```
cd <project-name>
cd kernel
make ARCH=arm64 kedge_defconfig android-10.config rk3399.config
make ARCH=arm64 rk3399-khadas-edge-android.img -j8
```

### Compiling android：
```
cd <project-name>
source build/envsetup.sh
lunch rk3399_Android10-userdebug
make installclean
make -j8
./mkimage.sh
```

### Pack update.img
```
cd <project-name>
source build/envsetup.sh
lunch rk3399_all-userdebug
./pack_image.sh
```