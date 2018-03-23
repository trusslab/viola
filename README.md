
Saeed Mirzamohammadi, Ardalan Amiri Sani, "Viola: Trustworthy Sensor Notifications for Enhanced Privacy on Mobile Systems
" in Proc. ACM MobiSys, June 2016
([PDF](http://www.ics.uci.edu/~saeed/Mirzamohammadi_MobiSys16.pdf)) ([Link to the video](https://www.youtube.com/watch?v=przL6tbIIgw)).

# People

* [Saeed Mirzamohammadi](http://www.ics.uci.edu/~saeed)
* [Ardalan Amiri Sani](http://www.ics.uci.edu/~ardalan)

In these instructions, we will show you how to set up Viola on Galaxy Nexus for _microphone -> led blinking_
invariant and Nexus5 for _camera -> vibrator_ invariant in Sections 1 and 2 respectively. You can also generate your own invariant check and also check out the proof in Section 3.

**Note: We have implemented our work based on Cyanogenmod. Cyanogenmod is discontinued. So we use the instructions for LineageOS which is its successor. In the instructions for LineageOS, simply replace every LineageOS with Cyanogenmod.


# 1. Viola on Galaxy Nexus


## 1.1 Compilation


Follow the instructions in the link below to build CyanogenMod For Google Galaxy Nexus (GSM) ("maguro") and apply the changes discussed below:
https://wiki.lineageos.org/devices/maguro/build


We have built Viola on top of CyanogenMod version 10.1.3-RC1. So you have to apply the following changes in section 4.5 (Thanks to Seunghyun Choi):

* Use the following instruction for initializing repo:

```sh
repo init -u https://github.com/CyanogenMod/android.git -b cm-10.1 -m cm-10.1.3-RC1.xml
```

* Go to .repo/manifasts/cm-10.1.3-RC1.xml file and find the project path "external/svox". Then change the line to the following:

```sh
<project path="external/svox" name="platform/external/svox" groups="pdk-cw-fs" remote="aosp" revision="refs/tags/android-4.2.2_r1" />
```


## 1.2 Setting up the system

Change your current directory to the android system kernel directory and check out Viola repository using the following instructions:

```sh
cd ~/android/system/kernel/samsung/tuna
git add remote viola_origin https://github.com/trusslab/Viola_tuna_kernel.git
git checkout Viola_tuna_v1

cd ~/android/system/external/tinyalsa
git add remote viola_origin https://github.com/trusslab/Viola_tinyalsa.git
git checkout Viola_tinyalsa_v1
```


## 1.3 Usage note

The invariant implemented on Galaxy Nexus is the _microphone -> led blinking_ invariant. You can test it using a recorder application on your Galaxy Nexus.




# 2. Viola on Nexus5


## 2.1 Compilation


Follow the instructions here to build CyanogenMod For Google Nexus 5 ("hammerhead"):

https://wiki.lineageos.org/devices/hammerhead/build


## 2.2 Setting up the system


Change your current directory to the android system kernel directory and check out Viola repository using the following instructions:

```sh
cd ~/android/system/kernel/lge/hammerhead
git add remote viola_origin https://github.com/trusslab/Viola_hammerhead_kernel.git
git checkout Viola_hammerhead_v1
```

## 2.3 Usage note


The invariant implemented on Nexus5 is the _camera -> vibrator_ invariant. You can test it using a camera application on your Nexus5.


# 3. Implementation and proof of Viola's invariant checks


## 3.1 Downloading the files


Clone the source files with the command below:

```sh
git clone https://github.com/trusslab/Viola_InvariantChecks.git
```

## 3.2 Generating Checks


Follow the instructions on README file to build the Coq files and to generate the invariant checks for ARM. Once you generated the checks, you can replace your generated .S file with the .S file already existing in ~/kernel/viola/, in the main directory of your kernel repository and then edit the Makefile accordingly.

You can also go over the proof files using the Coq Proof Assistant: https://coq.inria.fr/download


