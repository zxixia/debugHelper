# debugHelper

## 1, Add to your project
* * *

> compile 'net.jiawa:net-jiawa-debughelper:1.0.0'


## 2, How to use it
* * *
### A, setup it in your main Activity.onCretea()
	XLog.setup(1, XLog.Flag(
		new XFlag(1, true,  "SubTag1"),
		new XFlag(2, false, "SubTag2"),
		new XFlag(3, true,  "SubTag3")
	));        
##### a, This means the whole log TAG is xixia-1.
##### b, Declare 3 sub tags, and only the subTag1 and subTag3 can work.

### B, use it to log where you want like follows:
	XLog.d(true, 1);
    XLog.d(true, 1, 3);
    XLog.d(true, 1, "Test subTag1", 3);

	XLog.d(true, 2);
    XLog.d(true, 2, 3);
    XLog.d(true, 2, "Test subTag2", 3);

	XLog.d(true, 3);
    XLog.d(true, 3, 3);
    XLog.d(true, 3, "Test subTag3", 3);

##### a, The first boolean controls this single log to show or not.
##### b, The second int means this log belongs to which sub tag. If the subTag is setup false, then this single log will not show.
##### c, You can just ouput some messages, or only some int nums, or both the messages and the int nums. Messages means some you want to log, nums means to show the call stack layers of this single log.

### C, preview looks like:
![Preview](https://github.com/zxixia/debugHelper/blob/master/pic/preview.png)

## 3, How to use publish to bintray
* * *

### A, sign up a account in (https://bintray.com/signup/oss)
### B, see this project [gradle-publish](https://github.com/msdx/gradle-publish)
##### a, copy the build.gradle to your project root directory
##### b, copy and change the values in gradle.properties to your project root directory
##### c, copy the bintray.gradle to your app directory
##### d, add the follows code to your app/build.gradle
    // This script was used to upload files to bintray.
    // Note: please put it on the bottm.
    apply from: 'bintray.gradle'
### C, after success build your project, input the following commands in your AndroidStudio command ternimal
    gradlew javadocJar
    gradlew sourcesJar
    gradlew install
    gradlew bintrayUpload