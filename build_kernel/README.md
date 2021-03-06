# Build amlogic-s9xxx kernel for Phicomm-N1 & S9xxx-Boxs

If you use Phicomm N1 & S9xxx-Boxs to install OpenWrt, you must know `Flippy`. He provides many versions of openwrt firmware for Phicomm-N1 & S9xxx-Boxs and shares his series of Amlogic S9xxx kernels.

## Usage

You can install Flippy’s OpenWrt firmware and use it. If you want to define some plug-ins and make your own dedicated OpenWrt firmware, you can use this script to generate a kernel package adapted to this github source code. You have two ways to get the kernel, one is to use the ***`Flippy’s *.img file`*** provided by him to extract. another way is to use the kernel files provided by Flippy to synthesize ***`(boot-${flippy_version}.tar.gz, dtb-amlogic-${flippy_version}.tar.gz & modules-${flippy_version}.tar.gz)`***. The operation of these two methods is as follows:

The first method: 
```shell script
Example: ~/build-kernel/
 ├── flippy
 │   ├── N1_Openwrt*.img                   # Recommend Use Flippy's N1_Openwrt.img files
 │   ├── OR: S9***_Openwrt*.img            # Use Flippy's S9***_Openwrt*.img files
 │   └── OR: Armbian*Aml-s9xxx*.img        # Use Flippy's Armbian*.img files
 └── make_use_img.sh
```

Put the ***`Flippy’s *.img file`*** E.g: ***`N1_Openwrt*.img`*** file into the ***`${flippy_folder}`*** folder, Modify ${flippy_file} to kernel file name. E.g: ***`flippy_file="N1_Openwrt_R20.10.20_k5.9.5-flippy-48+.img"`***. ( If the file of ${flippy_file} is not found, Will search for other *.img and *.img.xz files in the ${flippy_folder} directory. ) then run the script:
```shell scriptt
sudo ./make_use_img.sh
```

The second method: 
```shell script
Example: ~/build-kernel/
 ├── flippy
 │   ├── boot-5.9.5-flippy-48+.tar.gz
 │   ├── dtb-amlogic-5.9.5-flippy-48+.tar.gz
 │   └── modules-5.9.5-flippy-48+.tar.gz
 └── make_use_kernel.sh
```

put ***`boot-${flippy_version}.tar.gz, dtb-amlogic-${flippy_version}.tar.gz & modules-${flippy_version}.tar.gz`*** the three files into the ***`${flippy_folder}`*** folder, Modify ${flippy_version} to kernel version. E.g: ***`flippy_version="5.9.5-flippy-48+"`***. ( If the files of ${flippy_version} is not found, Will search for other files in the ${flippy_folder} directory. ) then run the script:
```shell script
sudo ./make_use_kernel.sh
```

The generated files ***` kernel.tar.xz & modules.tar.xz `*** will be directly placed in the kernel directory of this github: ***` ~/armbian/kernel-amlogic/kernel/${build_save_folder} `***

## Update and supplement dtb file

Update kernel.tar.xz files in the kernel directory with the latest dtb file.
```shell script
sudo ./update_dtb.sh
```

