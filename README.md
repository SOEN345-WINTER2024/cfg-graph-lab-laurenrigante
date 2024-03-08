

# lauren rigante
40188593


STEP 1-6 CALCULATOR APP

step 1) control flow graph

<img width="393" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/3b3c7632-3699-455d-a834-81ce0803ebb2">



step 2) node coverage
<img width="250" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/0e116dd0-a7d7-44a0-b689-98584d3dcd3a">


step 3) edge coverage
<img width="394" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/7a5d6e43-2738-4b56-8b60-7eb2d017cb9c">



step 4) edge-pair coverage
<img width="455" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/555ef029-0b6e-48c9-8210-ddc7de4d9884">


step 5)  event flow graph
<img width="255" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/3a8e5a8d-03da-422e-8a51-6924ae40262a">

step 6)



# For selected app -- antimine

Step 1) control flow graph
<img width="320" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/a6fcac5f-eecb-4532-acea-71bfc68ccf75">

step 2) node coverage
<img width="178" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/9353037c-4ec3-45c9-964f-d85a47625d6f">

step 3) edge coverage
<img width="206" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/444198ad-1c6a-438c-9741-c70dc148d94c">

step 4) edge pair coverage
<img width="398" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/ac6749b7-0736-4729-9f84-5a149648941c">

step 5) event flow graph
<img width="241" alt="image" src="https://github.com/SOEN345-WINTER2024/cfg-graph-lab-laurenrigante/assets/93160873/4c2e1e5e-47d3-4267-b013-c5a89f252a92">








___
# Soot Tutorial
[![Build Status](https://travis-ci.com/noidsirius/SootTutorial.svg?branch=master)](https://travis-ci.com/noidsirius/SootTutorial)
[![Gitpod ready-to-code](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/noidsirius/SootTutorial)
[![Docker Pull](https://img.shields.io/docker/pulls/noidsirius/soot_tutorial)](https://hub.docker.com/r/noidsirius/soot_tutorial)


This repository contains (will contain) several simple examples of static program analysis in Java using [Soot](https://github.com/Sable/soot).

## Who this tutorial is for?
Anybody who knows Java programming and wants to do some static analysis in practice but does not know anything about Soot and static analysis in theory.

If you have some prior knowledge about static program analysis I suggest you learn Soot from [here](https://github.com/Sable/soot/wiki/Tutorials).

### [Why another tutorial for Soot?](docs/Other/Motivation.md)

## Setup
In short, use Java 8 and run `./gradlew build`. For more information and Docker setup, follow this [link](docs/Setup/). 

## Chapters
### 1: Get your hands dirty

In this chapter, you will visit a very simple code example to be familiar with Soot essential data structures and **Jimple**, Soot's principle intermediate representation.

* `./gradlew run --args="HelloSoot"`: The Jimple representation of the [printFizzBuzz](demo/HelloSoot/FizzBuzz.java) method alongside the branch statement.
* `./gradlew run --args="HelloSoot draw"`: The visualization of the [printFizzBuzz](demo/HelloSoot/FizzBuzz.java) control-flow graph.



|Title |Tutorial | Soot Code        | Example Input  |
| :---: |:-------------: |:-------------:| :-----:|
|Hello Soot |[Doc](docs/1/)      | [HelloSoot.java](src/main/java/dev/navids/soottutorial/hellosoot/HelloSoot.java) | [FizzBuzz.java](demo/HelloSoot/FizzBuzz.java) |

<img src="docs/1/images/cfg.png" alt="Control Flow Graph" width="400"/>

### 2: Know the basic APIs

In this chapter, you get familiar with some basic but useful methods in Soot to help read, analyze, and even update java code.

* `./gradlew run --args="BasicAPI"`: Analyze the class [Circle](demo/BasicAPI/Circle.java).
* `./gradlew run --args="BasicAPI draw"`: Analyze the class [Circle](demo/BasicAPI/Circle.java) and draws the call graph.

|Title |Tutorial | Soot Code        | Example Input  |
| :---: |:-------------: |:-------------:| :-----:|
|Basic API |[Doc](https://medium.com/@noidsirius/know-the-basic-tools-in-soot-18f394318a9c)| [BasicAPI.java](src/main/java/dev/navids/soottutorial/basicapi/BasicAPI.java) | [Circle](demo/BasicAPI/Circle.java) |


<img src="docs/2/images/callgraph.png" alt="Call Graph" width="400"/>

### 3: Android Instrumentation

In this chapter, you learn how to insert code into Android apps (without having their source code) using Soot. To run the code, you need Android SDK (check this [link](docs/Setup/)).

* `./gradlew run --args="AndroidLogger"`: Insert logging method calls at the beginning of APK methods of [Numix Calculator](demo/Android/calc.apk).
* `./gradlew run --args="AndroidClassInjector"`: Create a new class from scratch and inject it to the  [Numix Calculator](demo/Android/calc.apk).

The instrumented APK is located in `demo/Android/Instrumented`. You need to sign it in order to install on an Android device:
```sh
cd ./demo/Android
# on Windows, replace 'sign.sh' by 'sign.ps1'
./sign.sh Instrumented/calc.apk key "android"
adb install -r -t Instrumented/calc.apk
```
To see the logs, run `adb logcat | grep -e "<SOOT_TUTORIAL>"`

|Title |Tutorial | Soot Code        | Example APK|
| :---: |:-------------: |:-------------:| :-----:|
|Log method calls in an APK| [Doc](https://medium.com/@noidsirius/instrumenting-android-apps-with-soot-dd6f146ff4d2)| [AndroidLogger.java](src/main/java/dev/navids/soottutorial/android/AndroidLogger.java) | [Numix Calculator](demo/Android/calc.apk) (from [F-Droid](https://f-droid.org/en/packages/com.numix.calculator/))|
|Create and inject a class into an APK| [Doc](https://medium.com/@noidsirius/instrumenting-android-apps-with-soot-dd6f146ff4d2) | [AndroidClassInjector.java](src/main/java/dev/navids/soottutorial/android/AndroidClassInjector.java) | [Numix Calculator](demo/Android/calc.apk) (from [F-Droid](https://f-droid.org/en/packages/com.numix.calculator/))|

<img src="docs/3/images/packs.png" alt="Soot Packs + Dexpler" width="400"/>

### 4: Call graphs and PointsTo Analysis in Android

This chapter gives you a brief overview o call graphs and PointsTo analysis in Android and you learn how to create calls graphs using FlowDroid. The source code of the example code is [here](demo/Android/STDemoApp). To run the code, you need Android SDK (check this [link](docs/Setup/)).

* `./gradlew run --args="AndroidCallGraph <CG_Algorithm> (draw)"`: Create the call graph of [SootTutorial Demo App](demo/Android/st_demo.apk) using `<CG_Algorithm>` algorithm and print information such as reachable methods or the number of edges.
    * `<CG_Algorithm>` can be `SPARK` or `CHA`
    * `draw` argument is optional, if provided a visualization of call graph will shown.
    * For example, `./gradlew run --args="AndroidCallGraph SPARK draw"` visualizes the call graph generated by SPARK algorithm.
* `./gradlew run --args="AndroidPTA"`: Perform PointsTo and Alias Analysis on [SootTutorial Demo App](demo/Android/st_demo.apk) using FlowDroid.

|Title |Tutorial | Soot Code        | Example APK|
| :---: |:-------------: |:-------------:| :-----:|
|Call graphs in Android| [Doc](https://medium.com/geekculture/generating-call-graphs-in-android-using-flowdroid-pointsto-analysis-7b2e296e6697)| [AndroidCallgraph.java](src/main/java/dev/navids/soottutorial/android/AndroidCallgraph.java) | [SootTutorial Demo App](demo/Android/st_demo.apk) ([source code](demo/Android/STDemoApp))|
|PointsTo Analysis in Android| [Doc](https://medium.com/geekculture/generating-call-graphs-in-android-using-flowdroid-pointsto-analysis-7b2e296e6697)| [AndroidPointsToAnalysis.java](src/main/java/dev/navids/soottutorial/android/AndroidPointsToAnalysis.java) | [SootTutorial Demo App](demo/Android/st_demo.apk) ([source code](demo/Android/STDemoApp))|

<img src="docs/4/images/Spark_CG.png" alt="The call graph of SootTutorial Demo app" width="400"/>



### 5: Some *Real* Static Analysis (:construction: WIP)

* `./gradlew run --args="UsageFinder 'void println(java.lang.String)' 'java.io.PrintStream"`: Find usages of the method with the given subsignature in all methods of [UsageExample.java](demo/IntraAnalysis/UsageExample.java).
* `./gradlew run --args="UsageFinder 'void println(java.lang.String)' 'java.io.PrintStream"`: Find usages of the method with the given subsignature of the given class signature in all methods of [UsageExample.java](demo/IntraAnalysis/UsageExample.java).


|Title |Tutorial | Soot Code        | Example Input  |
| :---: |:-------------: |:-------------:| :-----:|
|Find usages of a method| | [UsageFinder.java](src/main/java/dev/navids/soottutorial/intraanalysis/usagefinder/UsageFinder.java) | [UsageExample.java](demo/IntraAnalysis/usagefinder/UsageExample.java) |
|Null Pointer Analysis ||[NullPointerAnalysis](src/main/java/dev/navids/soottutorial/intraanalysis/npanalysis/) | [NullPointerExample.java](demo/IntraAnalysis/NullPointerExample.java) |

### 6: Interprocedural analysis (:construction: WIP)
|Title |Tutorial | Soot Code        | Example Input  |
| :---: |:-------------: |:-------------:| :-----:|
| | | | |
