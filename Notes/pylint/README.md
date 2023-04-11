# How to Pylint

In this guide, i will discuss how to incorporate `pylint` in your daily development workflow to write a code conforms to the google python style guide (at least they tried). 

## What is Pylint

It's a style and error checker to help you constantly check your code style against pylint (based on guildo, python creator's style check) to align with industry.

## How to install

Switch to the conda virtual environment for the project, `test_env`
```bash
conda activate test_env
```

Install the packge with conda, [reference](https://anaconda.org/anaconda/pylint)
```bash
conda install -c anaconda pylint
```

How you need to navigate in `terminal` or `git bash` to your working directory with `cd`

```bash
# change directory project
cd project

# change to directory "ndvi_calculator"
cd ndvi_calculator

# list all non-hidden files in current directory
ls .
# output looks like
>> my_awesome_code.py   README.md

# run pylint on your code
pylint --reports y my_awesome_code.py
```

Then you will have a report with:
- messages `pylint` gives you for this file
- some statitistics for the problems 



## Pylint messages explained!

Pylint will search in the following category

**Table of contents**
- [How to Pylint](#how-to-pylint)
  - [What is Pylint](#what-is-pylint)
  - [How to install](#how-to-install)
  - [Pylint messages explained!](#pylint-messages-explained)
    - [Message control](#message-control)
    - [output control](#output-control)
  - [Practionality (updating)](#practionality-updating)
  - [Reference](#reference)


|Symbol|Type|Desctiption|
|-|-|-|
|R|refactor|refactor for a good practice metric violation|
|C|convention|convention for coding standard violation|
|W|warning|warning for minor programming issues or stylistic problems|
|E|error|error for important programming issues (bugs)|
|F|fatal|fatal for errors which prevented further process (ur code doesn't run)|

For our team, we rank the priority into:
- F (must): if you have one F, code won't run
- E (must): if you have E, your code has bugs. Won't run.
- W (must): arguably optional
- C (elimite 80% of them): good convention you want to build your habit on such as `invalid-name` and `missing-function-docstring`
- R (optional): refactor, kinda optional


The goal is to make sure you don't have any Fatal, error, warning and as less as convention messages as possible.

> Tip: `pylint`'s naming style guide is [here](https://docs.pylint.org/options.html#naming-styles).


### Message control

The only tricky part is to selectively reduce `convention(C)` messages and `refactor(R)` messages.

Sometimes you have to write the code in the style `pylint` likes to make to have a higher score, but more often than not, `pylint`'s guide will be better than our own habit.    

Here is some command for message control.

```bash
# disable line-too-long message
pylint --disable=line-too-long my_awesome_code.py

# disable multiple messages
pylint --disable=import-error, line-too-long, invalid-name my_awesome_code.py

# display only error meeages
pylint -E my_awesome_code.py
```


### output control

You could also control the output to have a report, i recommend the following two options

```bash
# parsable format for reports to see the categoryly clearly
pylint --output-format=parseable my_awesome_code.py

# nice little format
pylint --output-format=parseable --reports y my_awesome_code.py
```

## Practionality (updating)

For practice, you won't get full mark for `pylint`. Some rule of thumbs you need to remember for are:
- no fatal, error or warning messages
- for convention and refactor messages, focus on message like
  - `invalid-name`
  - `missing-function-docstring`
  - `etc (keeps updating from now)`

## Reference

Some reference to learn more about `pylint`
- [offical pylint user manual](https://docs.pylint.org/index.html)
  - resourceful but not long as well
- [Real-Python pylint video tutorial](https://www.youtube.com/watch?v=fFY5103p5-c)
  - 17 mins video for basic intro of `pylint`

