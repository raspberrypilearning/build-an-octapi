# New project

Each project contains a set of directories for each language, you're set up now with an `en` directory that contains the necessary files to get you going.

* [meta.yml](#metayml)
* [Steps - step_1.md, step_2.md, etc](#steps)


## meta.yml

The `meta.yml` file sets lots of basic information for the project.

``` yml
title: The title of the project
hero_image: images/banner.png # The image used on the listing view
subtitle: Project subtitle # Used on the listing view
description: Project description # Used on the listing view
published: false # A boolean - `true` or`false` - that controls whether the project will appear on the listing view
steps: # A list of all the steps
  - title: How to get started # Used as the sidebar title for the step
    duration: 60 # Not used yet
```

## Steps

* [Links](#links)
* [Resources](#resources)
* [Images](#images)
* [Challenges](#challenges)
* [Definitions](#definitions)
* [Hints](#hints)
* [Collapsed ingredients](#collapsed-ingredients)

Project steps are written in the [Kramdown](https://kramdown.gettalong.org/) variety of markdown. There is a [quick reference guide](https://kramdown.gettalong.org/quickref.html) and [full syntax documentation](https://kramdown.gettalong.org/syntax.html). A [custom kramdown extension](https://github.com/RaspberryPiFoundation/kramdown_rpf) is used for hints, challenges & collapsed ingredients.

### Links, resources & images

See [kramdown documentation](https://kramdown.gettalong.org/quickref.html#links-and-images) for more details.

#### Links

A [link](http://kramdown.gettalong.org) to the kramdown homepage.

#### Resources

A [link to a file in the resources directory](resources/worksheet.pdf){:download='filename.pdf'}. The download part will make the file automatically download rather than be rendered in the browser, the filename you'd like the file to be saved with is the second bit after the `=`. The `/slash learning` application will ensure the resource is available.

#### Images

![Banner image](images/banner.png) - the link text becomes the alternative text for the image. The `/slash learning` application will ensure the image is available.

#### Challenges

``` markdown
--- challenge ---

## Challenge: Improving your drum

* Any markdown in here
* will be parsed as normal

--- /challenge ---
```


### Definitions

Definitions can be written using HTML abbreviations, which are a standard part of [kramdown](https://kramdown.gettalong.org/quickref.html#abbreviations)

```
To do this you might require a variable or a two word definition.

*[variable]: An object that has a name and stores a value.

*[two word]: Definitions are markdown, and can have [links](http://kramdown.gettalong.org) etc
```


### Hints

A header for the hint, and all the html markup for hints will be automatically added.

```
--- hints ---
--- hint ---

Here's a hint of how to do this project.

Any markdown you like within a hint:
* item 1
* item 2

--- /hint ---
--- hint ---
Hint 2

--- /hint ---
--- hint ---

Hint 3
--- /hint ---
--- hint ---
Hint 4
--- /hint ---

--- /hints ---
```

### Collapsed ingredients

Set the title and the image from within the `collapse` area. The image must exist in **this** project, not the ingredient.

--- collapse ---
---
title: Downloading and installing the Raspberry Pi software
image: images/scratch.png
---

[[[generic-scratch-new-project]]]

--- /collapse ---
