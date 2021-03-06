# Dagger Browser

Dagger Browser is a progressive web app for easily navigating a project's Dagger graph. The graph data is populated from a Dagger [SPI](https://dagger.dev/spi.html) plugin, and the browser is built using
[CRA (create-react-app)](https://github.com/facebook/create-react-app) with Typescript.

<img src="docs/plaid_screenshot.png" width="600" />

## Trying a sample

Check out the [demo site](https://snapchat.github.io/dagger-browser/plaid) built from the open source 
[Plaid](https://github.com/android/plaid) app.

The [plugin/sample](plugin/sample)
directory contains a fork of a [simple example](https://github.com/google/dagger/tree/master/examples/simple) from the Dagger repo. 

You can run `./run.sh` to generate the dagger components manifest for this example and display in the Dagger Browser.

## Using Dagger Browser in your app

To build a Dagger Browser site for your project, you'll need to (1) generate json files for your project's Dagger components, and (2) build the Dagger Browser app using that data.

To get started:

1. Add a dependency on `com.snap.daggerbrowser:daggerbrowser-processor` to any Gradle modules in project that process Dagger components:
```groovy
allprojects {
  repositories {
    mavenCentral()
  }
}
dependencies {
  kapt "com.snap.daggerbrowser:daggerbrowser-processor:0.6"
}  
```
2. Build your project. The plugin will generate json files for each Dagger component.
3. Checkout out the `dagger-browser` project
```
$: git clone git@github.com:Snapchat/dagger-browser.git
```
4. Build Dagger Browser using your generated json files:
```
cd dagger-browser
./run.sh ../my_project/
```
