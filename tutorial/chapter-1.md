---
title: Chapter 1—Getting Up and Running
position: 2

---

# Chapter 1—Getting Up and Running

In this chapter you're going to start with the basics, including installing the NativeScript CLI, starting a new project, and getting your first app up and running.

## Table of contents

- [1.1: Install NativeScript and configure your environment](#11-install-nativescript-and-configure-your-environment)
- [1.2: Start your app](#12-start-your-app)
- [1.3: Add target development platforms](#13-add-target-development-platforms)
- [1.4: Running your app](#14-running-your-app)
- [1.5: Development workflow](#15-development-workflow)

## 1.1: Install NativeScript and configure your environment

The NativeScript CLI has a few system requirements you must have in place before building NativeScript apps. As a first step, start by going through the instructions for your operating system:

- [Windows]({% slug windows %})
- [OS X]({% slug osx %})
- [Linux]({% slug linux %})

> **TIP**:
> * Completing the installation instructions can be tricky if you’re new to mobile development. If you get stuck, or you have questions at any point while going through this guide, the [NativeScript Community Slack channel](http://developer.telerik.com/wp-login.php?action=slack-invitation) is a great place to ask questions.
> * If you’re overwhelmed by these requirements, you may also be interested in using NativeScript as part of the [Telerik Platform](http://www.telerik.com/platform). The Telerik Platform provides robust tooling for NativeScript apps, including an IDE that performs iOS and Android builds in the cloud, removing the need to complete these system requirements.

After completing the setup you should have two commands available from your terminal: `tns`—which is short for <b>T</b>elerik <b>N</b>ative<b>S</b>cript—and `nativescript`. The two commands are equivalent, so we'll stick with the shorter `tns`.

You can verify the installation was successful by running `tns` in your terminal. You should see something like this:

```
$ tns
# NativeScript
┌─────────┬─────────────────────────────────────────────────────────────────────┐
│ Usage   │ Synopsis                                                            │
│ General │ $ tns <Command> [Command Parameters] [--command <Options>]          │
│ Alias   │ $ nativescript <Command> [Command Parameters] [--command <Options>] │
└─────────┴─────────────────────────────────────────────────────────────────────┘
```

## 1.2: Start your app

With the NativeScript CLI installed, it's time to start building your app. Normally, you would [use the `tns create` command to create an empty NativeScript application](https://github.com/NativeScript/NativeScript-cli#create-project). For this guide, we've scaffolded out a boilerplate project to act as a starting point for [Groceries](https://github.com/NativeScript/sample-Groceries).

<h4 class="exercise-start">
    <b>Exercise</b>: Get the Groceries starting point
</h4>

Navigate to a folder where you want to keep your app code:

<div class="no-copy-button"></div>

```
cd the-folder-you-want-groceries-to-be-in
```

Next, assuming you have [git installed](http://www.git-scm.com/), clone the Groceries repo from GitHub:

```
git clone https://github.com/NativeScript/sample-Groceries.git
```

After that, change to the newly cloned repo's folder:

```
cd sample-Groceries
```

Finally, switch to the “start” branch for this guide's starting point:

```
git checkout start
```

>**TIP:** The “end” branch has the final state of this guide's tutorial. Feel free to [refer to the branch on GitHub](https://github.com/NativeScript/sample-Groceries/tree/end) if you get stuck.

<div class="exercise-end"></div>

## 1.3: Add target development platforms

Your app is now set up, but before you run it, you need to initialize a platform-specific native project for each platform you intend to target.

<h4 class="exercise-start">
    <b>Exercise</b>: Add the iOS and Android platforms
</h4>

If you're on a Mac, start by adding the iOS platform:

```
tns platform add ios
```

Next, add the Android platform with the same `platform add` command:

```
tns platform add android
```

<div class="exercise-end"></div>

>**IMPORTANT:** You can add platforms only for SDKs that you already have installed on your development machine. If you get errors running `tns platform add`, refer back to the section on [setting up your development environment](#install-nativescript-and-configure-your-environment).

The `platform add` command adds a folder called `platforms` to your project, and copies all of the required native SDKs into this folder. When you build the application, the NativeScript CLI will copy your application code into the `platforms` folder so that a native binary can be created.

## 1.4: Running your app

With the platform initialization complete, you can run your app in an emulator or on devices.

<h4 class="exercise-start">
    <b>Exercise</b>: Run your app
</h4>

If you're on a Mac, start by running the app in an iOS simulator with the following command:

```
tns run ios --emulator
```

If all went well, you should see something like this:

![iOS login]({{site.baseurl}}/img/cli-getting-started/nativescript/chapter1/ios/1.png)

Next, run your app on an Android emulator with the following command:

```
tns run android --emulator
```

> **WARNING**:
> * You must have at least one Android AVD (Android Virtual Device) configured for this command to work. If you get an error, try [setting up an AVD](http://developer.telerik.com/featured/using-android-emulator-hybrid-mobile-apps-telerik-appbuilder/#managing-avds) and then run the command again.
> * If you're using [Genymotion](https://www.genymotion.com), launch your Genymotion virtual device, and then run `tns run android`.

If all went well, you should see your app running in an Android emulator:

![Android login]({{site.baseurl}}/img/cli-getting-started/nativescript/chapter1/android/1.png)

<div class="exercise-end"></div>

Here are a few other tips for running NativeScript apps.

> **TIP**:
> * To run on a USB-connected Android or iOS device, use the same `run` command without the `--emulator` flag—i.e. `tns run android` and `tns run ios`.
> * The `tns device` command lists all USB-connected iOS devices, USB-connected Android devices, and Genymotion virtual devices that `tns run` can deploy to. Note that `tns device` does not list iOS simulators.

## 1.5: Development workflow

At this point, you have the NativeScript CLI downloaded and installed, as well as the iOS and Android dependencies that you need to run your app. Now you need a good workflow that lets you make changes and see results fast.

A good way to see your changes is to execute `tns run ios` or `tns run android` after you save files. To see this action, let's make a trivial update to your app.

<h4 class="exercise-start">
    <b>Exercise</b>: Your first NativeScript change
</h4>

If your previous `tns run ios` or `tns run android` task is still running, type `Ctrl+C` in your terminal to kill it.

Open your app's `app/views/login/login.xml` file in your text editor of choice and change `<Label text="hello world" />` to `<Label text="hello NativeScript" />`.

Return to your terminal and run either `tns run ios --emulator` (if you're on a Mac), or `tns run android --emulator`. You should see the app relaunch and the updated text displayed.

<div class="exercise-end"></div>

As you might have noticed, the `tns run` command blocks your terminal while your app is running (it's the task you had to use `Ctrl` + `C` to kill). The task shows both the output of `console.log()` statements as your app executes, as well as stack traces when things go wrong. So if your app crashes at any time during this guide, look to the terminal for a detailed report of the problem.

The iOS and Android logs can be a bit noisy, so you might have to scroll up a bit to find the actual problem. For example if I try to call `foo.bar()` when `foo` does not exist, here's the information I get on iOS:

```
/app/path/to/file.js:14:8: JS ERROR ReferenceError: Can't find variable: foo
1   0xe3dc0 NativeScript::FFICallback<NativeScript::ObjCMethodCallback>::ffiClosureCallback(ffi_cif*, void*, void**, void*)
```

And here's the same information in the Android logs:

```
E/TNS.Native( 2063): ReferenceError: foo is not defined
E/TNS.Native( 2063): File: "/data/data/org.nativescript.groceries/files/app/./views/login/login.js, line: 13, column: 4
```

> **TIP**: When you're trying to debug a problem, you can also try adding `console.log()` statements in your JavaScript code—exactly as you would in a browser-based application.

If you find it tedious to continuously run `tns run` from the terminal, you may be interested in using `tns livesync` instead. The `tns livesync` command instantly transfers XML, CSS, and JavaScript files to a running NativeScript app. If you set the command's `--watch` flag (`tns livesync ios --emulator --watch` or `tns livesync android --emulator --watch`), the NativeScript CLI will watch your app for changes, and apply those changes automatically after you save files. Be warned, however, that the `livesync` command does not show `console.log()` output or stack traces on iOS simulators. So during iOS debugging you may want to switch back to `tns run`.

Now that you've created an app, configured your environment, and set up your app to run on iOS and Android, you're ready to start digging into the files that make up a NativeScript app.

<div class="next-chapter-link-container">
  <a href="/tutorial/chapter-2">Continue to Chapter 2—Building the UI</a>
</div>