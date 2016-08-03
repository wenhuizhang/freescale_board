# freescale_board


http://www.nxp.com/products/software-and-tools/software-development-tools/i.mx-software-and-tools/i.mx-6-series-software-and-development-tool-resources:IMX6_SW?#overview

### Add library: 

```
sudo apt-get install uuid uuid-dev zlib1g-dev liblz-dev liblzo2-2 liblzo2-dev lzop git-core curl u-boot-tools mtd-utils android-tools-fsutils openjdk-7-jdk

```

Check java version 

```
$ sudo update-alternatives --config java
$ sudo update-alternatives --config javac
```


```


sudo apt-get install git-core gnupg flex bison gperf build-essential \
  zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
  lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
  libgl1-mesa-dev libxml2-utils xsltproc unzip
  
  

```


configure USB: 

`$ wget -S -O - http://source.android.com/source/51-android.rules | sed "s/<username>/$USER/" | sudo tee >/dev/null /etc/udev/rules.d/51-android.rules; sudo udevadm control --reload-rules`



### To get the Android source code from Google repo, follow the steps below:
```
$ cd ~
$ mkdir myandroid
$ mkdir bin
$ cd myandroid
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
$ ~/bin/repo init -u https://android.googlesource.com/platform/manifest -b android-6.0.1_r22
$ ~/bin/repo sync # This command loads most needed repos. Therefore, it can take several
hours to load.

```
### Get M6.0.1_2.0.0 kernel source code from Freescale open source git:
```
cd ~/myandroid
git clone git://git.freescale.com/imx/linux-2.6-imx.git kernel_imx
cd kernel_imx
git checkout m6.0.1_2.0.0-ga
```


### If you use U-Boot as your bootloader, clone the U-Boot git repository from the open source git:
```
cd ~/myandroid/bootable
mkdir bootloader
cd bootloader
git clone git://git.freescale.com/imx/uboot-imx.git uboot-imx
cd uboot-imx
git checkout m6.0.1_2.0.0-ga

```


### Assume you have unzipped the i.MX Android release package to `<save-dir>/android_M6.0.1_2.0.0_source` .
```
$ cd ~/myandroid
$ source ~/Documents/android_M6.0.1_2.0.0_source/code/M6.0.1_2.0.0/and_patch.sh
$ help
```
### You should see that the "c_patch" function is available.
```
$ c_patch ~/Documents/android_M6.0.1_2.0.0_source/code/M6.0.1_2.0.0/ imx_M6.0.1_2.0.0

```

### If everything is OK, "c_patch" generates the following output to indicate the successful patch:
```
*****************************************************************
Success: Now you can build the Android code for FSL i.MX platform
*****************************************************************
```

## An example for the SABRE Board for Smart Devices i.MX 6Dual/Quad is:
```
cd ~/myandroid
source build/envsetup.sh
lunch sabresd_6dq_user
make
```



## Mount 

```

sudo dd if=/dev/zero of=/dev/sdd bs=8192

cd ~/myandroid/

sudo chmod +x ./device/fsl/common/tools/fsl-sdcard-partition.sh

cd /home/wenhui/myandroid/out/target/product/sabresd_6dq
sudo ./../../../../../../wenhui/myandroid/device/fsl/common/tools/fsl-sdcard-partition.sh  -f imx6q /dev/sdd



```


