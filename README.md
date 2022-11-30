# SplitIO-BGTaskScheduler-register
Two example projects using SplitIO iOS SDK from app extension


In this example I provide two projects including an iOS application with an iMessage Extension target
Both issues I describe here can be reproduce when running each project

## Project 1 - Cocoapods
In this project I have incorporated Split iOS SDK using Cocoapods.
I have added the framework for both the app and the extensions target so I can consume and use the split flags in both targets.
But when I'm building the iMessage Extensions target, I get a **compelation** error due to the usage of `BGTaskScheduler.shared.register` API in the `SplitBgSynchronizer` class - see iamge below 
<img width="1917" alt="Compilation-Error" src="https://user-images.githubusercontent.com/6380777/204866199-3bc4ab4c-004b-4ef1-8d7e-1c6a1fe19b35.png">

This is not expected behavior, as it prevents from actually build the project and using Split SDK within an extensions

### Project 2 - SPM
In this project I have incorporated Split iOS SDK using SPM.
I have added the framework for both the app and the extensions target so I can consume and use the split flags in both targets.

In this repo I encounter a **runtime error (crash)** when I call that specific API in `SplitBgSynchronizer.schedule` which is more adaquat as.
I don't know if you can have a compilation time protection when using that API, or some way to test if it is available to use when called to prevent that crash.

<img width="1911" alt="Runtime-Crash" src="https://user-images.githubusercontent.com/6380777/204867595-390e8e54-d38c-48ff-b530-3ceefb2f1274.png">


But I guess it is OK, as I don't expect Extensions to schedule background tasks, and a runtime error could explain a developer on his/hers mistake
