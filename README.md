# Lune's Official Kotlin Style Guide

This style guide is different from others you may see, because the focus is centered on readability for print and the web. We created this style guide to keep the code in our tutorials consistent.

Our overarching goals are **conciseness**, **readability** and **simplicity**.

You should also check out our other style guides:

- [Swift](https://github.com/Lune-Technologies/swift-style-guide)
- [Objective-C](https://github.com/kodecocodes/objective-c-style-guide)
- [Java](https://github.com/kodecocodes/java-style-guide)

## Inspiration

This style-guide is somewhat of a mash-up between the existing Kotlin language style guides, and a tutorial-readability focused Swift style-guide. The language guidance is drawn from:

- The [Android Kotlin style guide](https://android.github.io/kotlin-guides/style.html)
- The [Kotlin Coding Conventions](https://kotlinlang.org/docs/reference/coding-conventions.html)
- The [Android contributors style guide](https://source.android.com/source/code-style.html)
- The [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html).

Alterations to support additional readability in tutorials were inspired by the [Lune Swift style guide](https://github.com/Lune-Technologies/swift-style-guide).

## Android Studio Coding Style

It is possible to get Android Studio to adhere to these style guidelines, via a rather complex sequence of menus. To make it easier, we've provided a coding style that can be imported into Android Studio.

The file can be found [here](https://koenig-media.raywenderlich.com/uploads/2018/03/rwstyle.xml_.zip).

To install the file, open Android Studio Settings and go to **Editor > Code Style > Kotlin**, then click the gear menu and choose **Import Scheme...**.

From now on, projects you create _should_ follow the correct style guidelines.

## Table of Contents

- [Nomenclature](#nomenclature)
  - [Packages](#packages)
  - [Classes & Interfaces](#classes--interfaces)
  - [Methods](#methods)
  - [Fields](#fields)
  - [Variables & Parameters](#variables--parameters)
  - [Misc](#misc)
- [Declarations](#declarations)
  - [Visibility Modifiers](#visibility-modifiers)
  - [Fields & Variables](#fields--variables)
  - [Classes](#classes)
  - [Data Type Objects](#data-type-objects)
  - [Enum Classes](#enum-classes)
- [Spacing](#spacing)
  - [Indentation](#indentation)
  - [Line Length](#line-length)
  - [Vertical Spacing](#vertical-spacing)
- [Semicolons](#semicolons)
- [Getters & Setters](#getters--setters)
- [Brace Style](#brace-style)
- [When Statements](#when-statements)
- [Annotations](#annotations)
- [Types](#types)
  - [Type Inference](#type-inference)
  - [Constants vs. Variables](#constants-vs-variables)
  - [Optionals](#optionals)
- [XML Guidance](#xml-guidance)
- [Language](#language)
- [Copyright Statement](#copyright-statement)
- [Smiley Face](#smiley-face)
- [Credit](#credits)

## Nomenclature

On the whole, naming should follow Java standards, as Kotlin is a JVM-compatible language.

### Packages

Package names are similar to Java: all **lower-case**, multiple words concatenated together, without hypens or underscores:

**BAD**:

```kotlin
com.YourCompany.funky_widget
```

**GOOD**:

```kotlin
com.yourcompany.funkywidget
```

### Classes & Interfaces

Written in **UpperCamelCase**. For example `RadialSlider`.

### Methods

Written in **lowerCamelCase**. For example `setValue`.

### Fields

Generally, written in **lowerCamelCase**. Fields should **not** be named with Hungarian notation, as Hungarian notation is [erroneously thought](http://jakewharton.com/just-say-no-to-hungarian-notation/) to be recommended by Google.

Example field names:

```kotlin
class MyClass {
  var publicField: Int = 0
  val person = Person()
  private var privateField: Int?
}
```

Constant values in the companion object should be written in **uppercase**, with an underscore separating words:

```kotlin
companion object {
  const val THE_ANSWER = 42
}
```

### Variables & Parameters

Written in **lowerCamelCase**.

Single character values must be avoided, except for temporary looping variables.

### Misc

In code, acronyms should be treated as words. For example:

**BAD:**

```kotlin
XMLHTTPRequest
URL: String?
findPostByID
```

**GOOD:**

```kotlin
XmlHttpRequest
url: String
findPostById
```

## Declarations

### Visibility Modifiers

Only include visibility modifiers if you need something other than the default of public.

**BAD:**

```kotlin
public val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

**GOOD:**

```kotlin
val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

**GOOD:**

```kotlin
username: String
twitterHandle: String
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Data Type Objects

Prefer data classes for simple data holding objects.

**BAD:**

```kotlin
class Person(val name: String) {
  override fun toString() : String {
    return "Person(name=$name)"
  }
}
```

**GOOD:**

```kotlin
data class Person(val name: String)
```

### Enum Classes

Enum classes without methods may be formatted without line-breaks, as follows:

```kotlin
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```

## Spacing

Spacing is especially important in Lune code, as code needs to be easily readable as part of the tutorial.

### Indentation

Indentation is using spaces - never tabs.

#### Blocks

Indentation for blocks uses 2 spaces (not the default 4):

**BAD:**

```kotlin
for (i in 0..9) {
    Log.i(TAG, "index=" + i)
}
```

**GOOD:**

```kotlin
for (i in 0..9) {
  Log.i(TAG, "index=" + i)
}
```

#### Line Wraps

Indentation for line wraps should use 4 spaces (not the default 8):

**BAD:**

```kotlin
val widget: CoolUiWidget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

**GOOD:**

```kotlin
val widget: CoolUiWidget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

### Line Length

Lines should be no longer than 100 characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity and organization. Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.

## Comments

When they are needed, use comments to explain **why** a particular piece of code does something. Comments must be kept up-to-date or deleted.

Avoid block comments inline with code, as the code should be as self-documenting as possible. _Exception: This does not apply to those comments used to generate documentation._

## Semicolons

Semicolons ~~are dead to us~~ should be avoided wherever possible in Kotlin.

**BAD**:

```kotlin
val horseGiftedByTrojans = true;
if (horseGiftedByTrojans) {
  bringHorseIntoWalledCity();
}
```

**GOOD**:

```kotlin
val horseGiftedByTrojans = true
if (horseGiftedByTrojans) {
  bringHorseIntoWalledCity()
}
```

## Getters & Setters

Unlike Java, direct access to fields in Kotlin is preferred.

If custom getters and setters are required, they should be declared [following Kotlin conventions](https://kotlinlang.org/docs/reference/properties.html) rather than as separate methods.

## Brace Style

Only trailing closing-braces are awarded their own line. All others appear the same line as preceding code:

**BAD:**

```kotlin
class MyClass
{
  fun doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

**GOOD:**

```kotlin
class MyClass {
  fun doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required.

**BAD:**

```kotlin
if (someTest)
  doSomething()
if (someTest) doSomethingElse()
```

**GOOD:**

```kotlin
if (someTest) {
  doSomething()
}
if (someTest) { doSomethingElse() }
```

## When Statements

Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

**BAD:**

```kotlin
when (anInput) {
  1 -> doSomethingForCaseOneOrTwo()
  2 -> doSomethingForCaseOneOrTwo()
  3 -> doSomethingForCaseThree()
}
```

**GOOD:**

```kotlin
when (anInput) {
  1, 2 -> doSomethingForCaseOneOrTwo()
  3 -> doSomethingForCaseThree()
  else -> println("No case satisfied")
}
```

## Types

Always use Kotlin's native types when available. Kotlin is JVM-compatible so **[TODO: more info]**

### Type Inference

Type inference should be preferred where possible to explicitly declared types.

**BAD:**

```kotlin
val something: MyType = MyType()
val meaningOfLife: Int = 42
```

**GOOD:**

```kotlin
val something = MyType()
val meaningOfLife = 42
```

### Constants vs. Variables

Constants are defined using the `val` keyword, and variables with the `var` keyword. Always use `val` instead of `var` if the value of the variable will not change.

_Tip_: A good technique is to define everything using `val` and only change it to `var` if the compiler complains!

### Nullable Types

Declare variables and function return types as nullable with `?` where a `null` value is acceptable.

Use implicitly unwrapped types declared with `!!` only for instance variables that you know will be initialized before use, such as subviews that will be set up in `onCreate` for an Activity or `onCreateView` for a Fragment.

When naming nullable variables and parameters, avoid naming them like `nullableString` or `maybeView` since their nullability is already in the type declaration.

When accessing a nullable value, use the safe call operator if the value is only accessed once or if there are many nullables in the chain:

```kotlin
editText?.setText("foo")
```

## XML Guidance

Since Android uses XML extensively in addition to Kotlin and Java, we have some rules specific to XML. These can be found in [Kodeco's Java code standards](https://github.com/kodecocodes/java-style-guide#xml-guidance)

## Language

Use `en-US` English spelling. 🇺🇸

**BAD:**

```kotlin
val colourName = "red"
```

**GOOD:**

```kotlin
val colorName = "red"
```

## Copyright Statement

The following copyright statement should be included at the top of every source file:

```
/*
 * Copyright (c) 2023 Lune® Technologies Ltd.
 *
 * Permission is hereby granted, free of charge, to any person obtaining a copy
 * of this software and associated documentation files (the "Software"), to deal
 * in the Software without restriction, including without limitation the rights
 * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 * copies of the Software, and to permit persons to whom the Software is
 * furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice shall be included in
 * all copies or substantial portions of the Software.
 *
 * Notwithstanding the foregoing, you may not use, copy, modify, merge, publish,
 * distribute, sublicense, create a derivative work, and/or sell copies of the
 * Software in any work that is designed, intended, or marketed for pedagogical or
 * instructional purposes related to programming, coding, application development,
 * or information technology.  Permission for such use, copying, modification,
 * merger, publication, distribution, sublicensing, creation of derivative works,
 * or sale is expressly withheld.
 *
 * This project and source code may use libraries or frameworks that are
 * released under various Open-Source licenses. Use of those libraries and
 * frameworks are governed by their own individual licenses.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 * THE SOFTWARE.
 */
```

## Smiley Face

As encouraged by [Kodeco](https://www.kodeco.com/), smiley faces are a very prominent style feature for [Lune](https://www.lunedata.io/)! It is very important to have the correct smile signifying the immense amount of happiness and excitement for the coding topic. The closing square bracket `]` is used because it represents the largest smile able to be captured using ASCII art. A closing parenthesis `)` creates a half-hearted smile, and thus is not preferred.

Bad:

    :)

Good:

    :]

## Credits

This style guide is a collaborative effort from the most stylish
kodeco.com team members:

- [Darryl Bayliss](https://github.com/DarrylBayliss)
- [Tom Blankenship](https://github.com/tgblank)
- [Sam Davies](https://github.com/sammyd)
- [Mic Pringle](https://github.com/micpringle)
- [Ellen Shapiro](https://github.com/designatednerd)
- [Ray Wenderlich](https://github.com/rwenderlich)
- [Joe Howard](https://github.com/orionthwake)
