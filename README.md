# ex.dagger

A simple example project that uses
- [IntelliJ](https://www.jetbrains.com/idea/) IDE Version 2018.4
- [Gradle](https://gradle.org) version 4 
  - [Gradle apt-idea plugin](https://github.com/tbroyer/gradle-apt-plugin#intellij-idea)
- [Dagger2 ](https://google.github.io/dagger/)

## Gradle setup

### apt-idea plugin
We use the [Gradle apt-idea plugin](https://github.com/tbroyer/gradle-apt-plugin#intellij-idea) which will take 
care to correctly configure the annotation processing, so that the processors are run automatically when
we start a gradle build, and it will also configure the [IntelliJ IDE](https://www.jetbrains.com/idea/) correctly, so that 
it finds the generated files and treats them as source files.

```gradle
plugins {
    id 'java'
    id 'net.ltgt.apt-idea' version "0.15"
}
```
### dagger dependency
With the apt-idea plugin in place, we can add the dagger-compiler to the apt configuration:

```gradle
final DAGGER_VER = '2.16'
dependencies {
    implementation "com.google.dagger:dagger:${DAGGER_VER}"
    apt "com.google.dagger:dagger-compiler:${DAGGER_VER}"
}
```

