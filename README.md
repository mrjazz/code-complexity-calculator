# Cyclomatic and Cognitive complextity examples

## Installation

I would prefer use it as global alias in my .bashrc or .zshrc configs:

```
alias complexity="php PATH_TO_PROJECT_DIR/bin/calculate-complexity.php $@"
```

After adding it in config, don't forget reload it, for example:

```
source ~/.zshrc
```

Then I can use it everywhere like that:

```
> complexity ./src
```

## What

This project contains PHP scripts that will allow you to calculate the
complexity of PHP code.

The complexity is calculated based on the following formula:

```
cognitive complexity * cyclomatic complexity = total complexity
```

Currently this project only calculates complexitiy at a (class) function level.

In order to calculate the complexity of a given piece of code, call the script
on the bin directory:

```
$ php ./bin/calculate-complexity.php ./src/*.php

           File : ./src/CognitiveComplexityScanner.php
        Methods : 1 = cy(1) * co(1)
                  6 = cy(3) * co(2)

           File : ./src/CyclomaticComplexityScanner.php
        Methods : 1 = cy(1) * co(1)
                  6 = cy(3) * co(2)
                  20 = cy(5) * co(4)
```

## Why

I got tired of people having unfounded opinions about what "readability" means.

There is [an interesting whitepaper](https://www.sonarsource.com/docs/CognitiveComplexity.pdf)
on this topic, which uses the term "Cognitive Complexity". As I could not find a
tool that allowed me to easily calculate both Cognitive and Cyclomatic
Complexity in an easy manner, I build one myself.

## How

I've basically just combined the logic behind two PHP Code Sniffs:

- `PHP_CodeSniffer\Standards\Generic\Sniffs\Metrics\CyclomaticComplexitySniff`
- `Symplify\CodingStandard\Sniffs\CleanCode\CognitiveComplexitySniff`

Instead of returning a true/false sort-of response when a given threshold is
crossed, I just made the code output a number.

## Who

This project has been created by [Potherca](https://twitter.com/potherca) and is
licensed under the [GNU GENERAL PUBLIC LICENSE v3](LICENSE)  (or higher):

```
/**
 * Copyright (c) 2019 Potherca
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation, version 3.
 *
 * This program is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 * General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program. If not, see <http://www.gnu.org/licenses/>.
 */
```