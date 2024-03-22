# ADB/Logcat Commands Cheat-Sheet

# ADB Commands Cheat-Sheet

| Description | Command | Notes |  |
| --- | --- | --- | --- |
| Navigate To Home Screen | adb shell am start -a android.intent.action.MAIN -c android.intent.category.HOME |  |  |
| Application Install | adb install TPLTRCU.apk |  |  |
| Application Uninstall | adb uninstall com.tpltrcu |  |  |
| To view apk properties | aapt dump badging <path-to-apk> |  |  |
| To Remove the Default Launcher | adb shell rm        /system/app/Launcher3.apk |  |  |
| Sort App disk usage by size | adb shell du /system/app | sort -k1,1 -n |  |  |
| Android Running Services | adb shell dumpsys activity services |  |  |
| Android Version | adb shell getprop ro.build.version.release |  |  |
| Android SDK Version | adb shell getprop ro.build.version.sdk |  |  |
| Android Get Properties | adb shell getpro |  |  |
| Android Set Property |  |  |  |
| Date & Time | adb shell date |  |  |
| Application Force-Stop | adb shell am force-stop <PACKAGE> |  |  |
| Running Processes | a |  |  |
| ADB Shell | adb shell |  |  |
| To get a file  | adb pull path_to_file |  |  |
| To put a file | adb push <sourcePath> <destinationPath> |  |  |
| To Change time Zone | adb shell setprop persist.sys.timezone "Asia/Kolkata" | http://en.wikipedia.org/wiki/List_of_tz_database_time_zones |  |
| To take backups | adb backup -apk -shared -all |  |  |
| To Restore | adb restore backup.ab |  |  |
| To save logs from android  | adb shell logcat > log.txt |  |  |
| To check CPU usage | adb shell dumpsys cpuinfo |  |  |
| To Check Memory usage | adb shell dumpsys meminfo |  |  |
| To Change Settings | adb shell am start -n com.android.settings/.Settings |  |  |
| Bug Report Via ADB   | adb bugreport > bug_report.txt |  |  |
| Bug Report Parsing | java -jar chkbugreport.jar bug_report.txt | https://github.com/sonyxperiadev/ChkBugReport/downloads  |  |
| To Reboot the OS | adb shell reboot |  |  |
| ADB Version | adb version |  |  |
| To get Help | adb help |  |  |
| To get Serial Number | adb get-serialno |  |  |
| List of devices | adb devices |  |  |
| To get running process | adb shell ps |  |  |
| To print dump | adb shell dumpsys |  |  |
| package version | adb shell dumpsys package packages | grep -E 'Package \[|versionName' | adb shell dumpsys package packages | grep -E 'Package \[|versionName' > /tmp/app-versions.txt |  |
| To start an Activity | adb shell am start PACKAGE_NAME/.ACTIVITY_NAME |  |  |
| To save screenshot | adb shell screencap -p > /mnt/image_name.png |  |  |
| List of installed packages | adb shell pm list packages --show-versioncode |  |  |
| To make key event | adb shell input keyevent <val> |  |  |
| List of running services | adb shell dumpsys activity services |  |  |
| Get Firmware Version | adb shell getprop http://ro.build.id/ |  |  |
| Factory Reset | adb shell am broadcast -a <package_name> -d 'ttm://factoryreset?source=user-local' |  |  |
| Change Environment | adb shell setprop <key> <value> |  |  |
| ADB multiple devices case | adb -s 192.168.232.2:5555 <command> | Use IP address  |  |

# Logcat Commands Cheat-Sheet

If you want to control the format of each log entry is dumped, you need to use the "adb logcat -v <format>" option, which supports the following formats:

| Description | Command | Notes |
| --- | --- | --- |
| Display priority/tag and the PID of process issuing the message (the default format) | adb logcat -v     brief |  |
| Display PID onlyadb logcat -v process |  |  |
| Display the priority/tag only | adb logcat -v tag |  |
| Display the raw log message, with no other metadata fields | adb logcat -v raw |  |
| Display the date, invocation time, priority/tag, and PID of the process issuing the message | adb logcat -v time |  |
| Display the priority, tag, and the PID and TID of the thread issuing the message  | adb logcat -v thread |  |
| Display the date, invocation time, priority, tag, and the PID and TID of the thread issuing the message | adb logcat -v threadtime |  |
| Display all metadata fields and separate messages with a blank lines | adb logcat -v long |  |

### Steps to remount and adb push

Here are the steps mount system_ext as readonly using userdebug builds and test an app in privileged mode:

From console or adb shell prompt use following steps:

### TTM push Commands using adb:

Ensure you are on a userdebug firmware build.

Commands using adb:

```
adb root
adb disable-verity
adb reboot
adb root
adb remount
adb push TTM.apk /system/app/TTM/
adb reboot
```

When the pushed apk is not needed anymore, it's important to enable verity again and reboot. This will revert back to preinstalled version of TTM and leave the system with verity enabled. This step is required to in order to be able to receive a firmware update. 

```
adb root
adb enable-verity
adb reboot
```

### Steps to check bootloader build

To verify run next adb command: `adb logcat | grep androidboot.bootloader`

Latest SEI commit are:

user build - 01.01.230829.154909

userdebug build - 01.01.230829.114718

# Key Codes for ADB Command "input keyevent"

0 -->  "KEYCODE_UNKNOWN"
1 -->  "KEYCODE_MENU"
2 -->  "KEYCODE_SOFT_RIGHT"
3 -->  "KEYCODE_HOME"
4 -->  "KEYCODE_BACK"
5 -->  "KEYCODE_CALL"
6 -->  "KEYCODE_ENDCALL"
7 -->  "KEYCODE_0"
8 -->  "KEYCODE_1"
9 -->  "KEYCODE_2"
10 -->  "KEYCODE_3"
11 -->  "KEYCODE_4"
12 -->  "KEYCODE_5"
13 -->  "KEYCODE_6"
14 -->  "KEYCODE_7"
15 -->  "KEYCODE_8"
16 -->  "KEYCODE_9"
17 -->  "KEYCODE_STAR"
18 -->  "KEYCODE_POUND"
19 -->  "KEYCODE_DPAD_UP"
20 -->  "KEYCODE_DPAD_DOWN"
21 -->  "KEYCODE_DPAD_LEFT"
22 -->  "KEYCODE_DPAD_RIGHT"
23 -->  "KEYCODE_DPAD_CENTER"
24 -->  "KEYCODE_VOLUME_UP"
25 -->  "KEYCODE_VOLUME_DOWN"
26 -->  "KEYCODE_POWER"
27 -->  "KEYCODE_CAMERA"
28 -->  "KEYCODE_CLEAR"
29 -->  "KEYCODE_A"
30 -->  "KEYCODE_B"
31 -->  "KEYCODE_C"
32 -->  "KEYCODE_D"
33 -->  "KEYCODE_E"
34 -->  "KEYCODE_F"
35 -->  "KEYCODE_G"
36 -->  "KEYCODE_H"
37 -->  "KEYCODE_I"
38 -->  "KEYCODE_J"
39 -->  "KEYCODE_K"
40 -->  "KEYCODE_L"
41 -->  "KEYCODE_M"
42 -->  "KEYCODE_N"
43 -->  "KEYCODE_O"
44 -->  "KEYCODE_P"
45 -->  "KEYCODE_Q"
46 -->  "KEYCODE_R"
47 -->  "KEYCODE_S"
48 -->  "KEYCODE_T"
49 -->  "KEYCODE_U"
50 -->  "KEYCODE_V"
51 -->  "KEYCODE_W"
52 -->  "KEYCODE_X"
53 -->  "KEYCODE_Y"
54 -->  "KEYCODE_Z"
55 -->  "KEYCODE_COMMA"
56 -->  "KEYCODE_PERIOD"
57 -->  "KEYCODE_ALT_LEFT"
58 -->  "KEYCODE_ALT_RIGHT"
59 -->  "KEYCODE_SHIFT_LEFT"
60 -->  "KEYCODE_SHIFT_RIGHT"
61 -->  "KEYCODE_TAB"
62 -->  "KEYCODE_SPACE"
63 -->  "KEYCODE_SYM"
64 -->  "KEYCODE_EXPLORER"
65 -->  "KEYCODE_ENVELOPE"
66 -->  "KEYCODE_ENTER"
67 -->  "KEYCODE_DEL"
68 -->  "KEYCODE_GRAVE"
69 -->  "KEYCODE_MINUS"
70 -->  "KEYCODE_EQUALS"
71 -->  "KEYCODE_LEFT_BRACKET"
72 -->  "KEYCODE_RIGHT_BRACKET"
73 -->  "KEYCODE_BACKSLASH"
74 -->  "KEYCODE_SEMICOLON"
75 -->  "KEYCODE_APOSTROPHE"
76 -->  "KEYCODE_SLASH"
77 -->  "KEYCODE_AT"
78 -->  "KEYCODE_NUM"
79 -->  "KEYCODE_HEADSETHOOK"
80 -->  "KEYCODE_FOCUS"
81 -->  "KEYCODE_PLUS"
82 -->  "KEYCODE_MENU"
83 -->  "KEYCODE_NOTIFICATION"
84 -->  "KEYCODE_SEARCH"
85 -->  "TAG_LAST_KEYCODE"

03-28 17:27:53.613  2020  2020 D ChannelBannerView: updateChannelInfo mCurrentChannel = Channel{id=-1, packageName=packageName, inputId=com.droidlogic.tvinput/.services.Hdmi3InputService/HW7, type=type, serviceType=, displayNumber=0, displayName=name, frequency=0, mServiceId=0, mTransportStreamId=0, mOriginalNetworkId=0, description=description, videoFormat=null, isPassthrough=true, browsable=true, mIsHidden=false, mIsSetHidden=false, mIsFavourite=false, mFavInfo=null, mSatelliteInfo=null, mTransponderInfo=null, searchable=true, locked=false, appLinkText=null, recordingProhibited=false, mContentRatings=null}

APK Signing:

apksigner sign --key platform.pk8 --cert platform.x509.pem app.apk
