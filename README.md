# ClojureScript for JavaScript Developers Starter Repo

This repo is a barebones starter for experimenting with ClojureScript. It's
written with the purpose of making it easy for JavaScript developers to get
started playing around with ClojureScript.

## Install Dependencies

### Java

To compile your ClojureScript you'll need a Java JDK. Don't worry, you won't
be writing any Java code, and, for the purposes of getting started, once you've
installed the JDK, you can entirely forget about Java.

Grab the latest JDK (version 10.0.1 as of the last update to this README) for
your operating system either from Oracle or OpenJDK:

- [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)
- [OpenJDK](http://openjdk.java.net/install/)

Verify that the JDK is installed correctly by running:

```
$ java -version
```

Now that you've got Java installed, you probably won't have to worry about it
on future projects.

### JS Dependencies

ClojureScript interops with JavaScript quite well, so we have access to the
npm ecosystem. One package we'll be using in particular is
[shadow-cljs](https://github.com/thheller/shadow-cljs), a project that provides
everything you need to compile your ClojureScript code with a focus on
simplicity and ease of use. Install it and other dependencies from within the
project via npm or Yarn:

```
# using npm
$ npm install

# using Yarn
$ yarn
```

Now that shadow-cljs is installed, we can invoke some of its commands:

```
# using npm
$ npx shadow-cljs help

# using Yarn
$ yarn shadow-cljs help
```

## Getting Started

The ClojureScript build configuration lives in this project's `shadow-cljs.edn`
file. You can think of this as somewhat analogous to a `webpack.config.js`. If
you'd like to learn more about how shadow-cljs works, you can follow it's
[user guide](https://shadow-cljs.github.io/docs/UsersGuide.html#_configuration).


Start shadow-cljs in dev mode by running the `watch` command:


```
# using npm
$ npx shadow-cljs watch app

# using Yarn
$ yarn shadow-cljs watch app
```

You should see some output and eventually a log statement letting you know that
the compilation has finished. Open your browser to `http://localhost:8020`.

### Writing Code

ClojureScript works off of namespaces that mirror the filepath. So, inside of
our `src` directory, we can see a `cljs_for_js_devs/core.cljs` file. If you
open that file, you'll see it declares a `cljs-for-js-devs.core` namespace. All
ClojureScript source files should follow this pattern.

Feel free to make changes to the core namespace and hit save. shadow-cljs will
pick up on those changes, recompile your code, and hot-reload your browser.

You're now all set-up to start writing ClojureScript code. You can install
libraries from npm just as you would on a JavaScript project via npm or Yarn.
See the shadow-cljs docs for how you can require them in your ClojureScript
source code: https://shadow-cljs.github.io/docs/UsersGuide.html#js-deps

If you'd like to explore native ClojureScript dependencies, simply add them
to the `dependencies` vector within the `shadow-cljs.edn` file. For example,
you can add the popular [cljs-time](https://github.com/andrewmcveigh/cljs-time)
library by updating the dependencies to:

```clj
{:dependencies
 [[com.andrewmcveigh/cljs-time "0.5.2"]]
```

### Using the REPL
Once you've got shadow-cljs building and your browser is running your app, you
can connect a ClojureScript REPL to it. This allows you to interact with your
source code and the connected browser direclty from your terminal:

```
# using npm
$ npx shadow-cljs cljs-repl app

# using Yarn
$ yarn shadow-cljs cljs-repl app
```

You should see a REPL prompt. Try writing some ClojureScript code:

```
[1:1]~cljs.user=> (println "Hi")
Hi
nil
```

Now, do it again, but this time keep an idea on your browser's console.
Amazingly, you'll see the string `"Hi"` printed there as well.

Now, add a function to your core namespace:

```clj
(defn say-hello []
  (println "hello..."))
```

Jump back over to your REPL and call the function:

```
[1:1]~cljs.user=> (require '[cljs-for-js-devs.core :as core])
nil
[1:1]~cljs.user=> (core/say-hello)
hello...
nil
```

Again, your both your REPL and browser should print out the `"hello..."`
message. Explore working the REPL so more, it's a core part of programming in
ClojureScript.
