---
layout: page
title: Night Writer
---

## Before You Begin

The idea of [Night Writing](https://en.wikipedia.org/wiki/Night_writing) was first developed for Napoleon's army so soldiers could communicate silently at night without light. The concept of night writing led to Louis Braille's development of his [Braille tactile writing system](https://en.wikipedia.org/wiki/Braille).

In this project we'll implement systems for generating Braille-like text from normal characters and the reverse.

### Simulating Braille

Braille uses a two-by-three grid of dots to represent characters. We'll simulate that concept by using three lines of symbols:

```
0.0.0.0.0.....00.0.0.00
00.00.0..0...00.0000..0
....0.0.0.....00.0.0...
```

The `0` represents a raised dot. The period is an unraised space. The above code reads "hello world" in normal text. You can experiment with [converting other words](http://www.euroblind.org/resources/braille-converter/) yourself and share some samples with your classmates.

Let's also constrain our our Braille files to eighty characters wide.

## Learning Goals / Areas of Focus

* Practice breaking a program into logical components
* Testing components in isolation and in combination
* Applying Enumerable techniques in a real context
* Reading text from and writing text to files

## Base Expectations

### An Interaction Model

The tool is used from the command line like so:

```
$ ruby ./lib/night_write.rb message.txt braille.txt
Created 'braille.txt' containing 256 characters
```

That will take the plaintext file `message.txt` and create a Braille simulation file `braille.txt`.

Then we can convert that Braille simulation back to normal text:

```
$ ruby ./lib/night_read.rb braille.txt output_message.txt
Created 'output_message.txt' containing 256 characters.
```

### Character Support

Use just the [lowercase letters a-z here from the American Foundation for the Blind](http://braillebug.afb.org/braille_print.asp) for your project.

## Development Phases

As you work to implement the project here are some ideas of how you might start into the problem:

### 1. The Runner

Write a Ruby program that can just output a string like:

```
$ ruby ./lib/night_write.rb message.txt braille.txt
Created 'braille.txt' containing 256 characters
```

Then work to:

* Pull the specified output filename from the command line arguments and put it into the string output
* Get the actual number of characters from the `message.txt` and output it in the message

### 2. Echo Characters

Your Braille-simulation file will need three lines of output for every one line of input. Generate output that is the same as your input line three times.

### 3. Mapping

You'll need a component, a "machine" if you will, where you can put in a normal character and get out the Braille equivalent. It's time to build that now.

### 4. Triple Replacement

Bringing together the Echo Characters idea with the Mapping idea, you can actually output your Braille characters to the file. Consider building a component that would take in a plain-text letter and a position (maybe numbered 0-5) and would return either a `0` or `.`.

### 5. Next Steps

About this point, you should try Braille-ifying a message and exchange it with a classmate. Are your outputs identical?

Then it's time to dive into the reading.

## Evaluation Rubric

The project will be assessed with the following rubric:

### 1. Overall Functionality

* 4: Application follows the complete spec and two extensions
* 3: Application converts to Braille and back successfully
* 2: Application only converts to Braille or from Braille
* 1: Application generates errors or crashes during normal usage

### 2. Fundamental Ruby & Style

* 4:  Application demonstrates excellent knowledge of Ruby syntax, style, and refactoring
* 3:  Application shows some effort toward organization but still has 6 or fewer long methods (> 8 lines) and needs some refactoring.
* 2:  Application runs but the code has many long methods (>8 lines) and needs significant refactoring
* 1:  Application generates syntax error or crashes during execution

### 3. Test-Driven Development

* 4: Application is broken into components which are well tested in both isolation and integration
* 3: Application uses tests to exercise core functionality, but has some gaps in coverage or leaves edge cases untested.
* 2: Application tests some components but has many gaps in coverage.
* 1: Application does not demonstrate strong use of TDD

### 4. Breaking Logic into Components

* 4: Application effectively breaks logical components apart with clear intent and usage
* 3: Application has multiple components with defined responsibilities but there is some leaking of responsibilities
* 2: Application has some logical components but divisions of responsibility are inconsistent or unclear and/or there is a "God" object taking too much responsibility
* 1: Application logic shows poor decomposition with too much logic mashed together
