---
layout: new-layouts/post
published: false
date: 2025-11-19 10:00:00
title: "How the Swift SDK for Android Works"
author: android-workgroup
category: "Developer Tools"
---

Since the announcement of [the preview Swift SDK for Android last month](/blog/nightly-swift-sdk-for-android/),
we've seen a lot of questions about how it works and what is missing. Read on for those answers.

Swift is a natively-compiled language to machine code and Android is no different.
That makes it on par with C and C++ code built using the Android NDK, which are
languages more geared towards performance, while Swift attempts a happier balance between
performance, safety, and usability. Swift apps must bundle a native runtime for
Android that implements many of its features, including its standard library and
core libraries like Dispatch and [Foundation](/blog/foundation-preview-now-available/).

However, since most Android platform APIs are only made available through Java
and Kotlin in the Java Virtual Machine (JVM), we need to use the Java Native
Interface (JNI) and write bindings both to call Swift from Java and go the
other way. That is where the swift-java project's `jextract` tool and its [new
support for generating such JNI bindings for you](/blog/gsoc-2025-showcase-swift-java/)
comes in. Please watch its author Mads Odgaard's [Server-Side Swift Conference talk from last month](https://www.youtube.com/watch?v=tOH6V1IvTAc)
and try out the tool for yourself with [this example Android app that he put together](https://github.com/swiftlang/swift-android-examples/tree/main/hello-swift-java).

- Should we add a paragraph talking about [the new #available features just added in trunk](https://forums.swift.org/t/getting-started-with-the-android-swift-sdk/80834/12)?

Swift on Android [first got started as soon as the language was open-sourced a decade ago](https://lists.swift.org/pipermail/swift-dev/Week-of-Mon-20151207/000171.html),
but it is by no means done. [The Android project board lists areas we are working on](https://github.com/orgs/swiftlang/projects/17)
and easy debugging is a high priority for us next. While it [appears to mostly work](https://github.com/swiftlang/llvm-project/issues/10831),
we need to test it more and make it easy to access. That will likely mean tying
the debugger and Swift Language Server Protocol tool, sourcekit-lsp, into editors
like [Visual Studio Code](/blog/gsoc-2025-showcase-swiftly-support-in-vscode/),
Android Studio, and [CodeEdit](https://www.codeedit.app/), another issue on our board.

A common concern is that we do not provide a cross-platform GUI toolkit. As we
write in [our draft vision document](https://github.com/swiftlang/swift-evolution/blob/807b844be42db582e434d1667fc907ae7a7a8775/visions/android.md),
the Android workgroup has no plans to ever create such a GUI toolkit, but will instead
curate a list of such cross-platform UI tools, everything from professional options
like [the Skip transpiler](https://skip.tools/) and [SCADE](https://www.scade.io/)
to open-source efforts like [FlutterSwift](https://github.com/PADL/FlutterSwift),
[SwiftGodot](https://github.com/migueldeicaza/SwiftGodot), and the in-progress
[SwiftCrossUI](https://swiftcrossui.dev/).

Finally, we intend to bring you interviews and information from those using Swift
on Android already, as pioneering companies like [Readdle](https://readdle.com/blog/swift-for-android-our-experience-and-tools)
and [Flowkey](https://medium.com/@ephemer/why-we-put-an-app-in-the-android-play-store-using-swift-96ac87c88dfc)
have been using Swift on Android for the last decade. The Left Bit's Pierluigi Cifani
gave [a great talk about their experiences at NSSpain 2025 a couple months ago](https://youtu.be/EIGl6GOo210)
and was [interviewed by Swift Toolkit last month](https://www.swifttoolkit.dev/posts/dc-pier).

Swift on Android has been a community effort for the last decade, snowballing
from that initial patch to many developers making their livelihood with
it today. Join us to make it even better!
