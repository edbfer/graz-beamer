# Documentation for the `graz` beamer template

The `graz` beamer template is a minimalist template for use in beamer presentations that takes inspiration from the branding used by the Karl-Franzens-Universität Graz.

In addition to the usual and necessary beamer defintions, the template also defines many new commands that can be used as tools in the presentations.

## List of Contents:
 0. [Compilation](#0-compilation)
 1. [Title Page](#1-title-page)
 2. [Images repository/handling](#2-image-repositoryhandling)
 3. [Miscellaneous](#3-miscellaneous)

## 0. Compilation

Best results are obtained when compiled with an advanced LaTeX engine like `lualatex` or  `XeLaTeX`. This template is/was developed using `lualatex`.

To use the template, just drop all the `.sty` files in the same folder as your main `.tex` file and tell beamer to load the template using: `\usetheme{graz}`-

## 1. Title Page

The title page of the `graz` beamer template has the following elements, which can be set using the respective setter functions:

| Element:       | Function:
| ------------- | --------------------- |
| title         | `\title`          |
| author        | `\author`         |
| co-authors    | `\secondauthors`  |
| date/location | `\date`           |               
| logo          | `\setlogopath`    |

## 2. Image repository/handling

### 2.1 Image repository

This beamer package defines some commands that make the organization of images/resouces in beamer presentations more manageable.

The main idea is that the user can define a path relative to which all images are loaded. In this way, it is possible to have a central repository with all the images/resources in a fixed place.

To set this path, the so-called **repository path**, the following function is used:

 `\setrepopath`: Sets the topmost path where images will be looked for.

The images located in the path set by the previous function can be retrieved by using the two following commands:

```latex
\loadfromrepo[optional]{filename}
```
This function is intended to be used as a direct replacement of the `\includegraphics` function from the `graphicx` package. All optional parameters work in the same way.

```latex
\loadtexfromrepo[optional]{filename}
```
This function works similarly to the previous one, but inputs a `tex` file (useful for the output of, for example, gnuplot with the cairolatex terminal). The `tex` file is wrapped in an `adjustbox` environment, which takes the optional parameters as arguments, resulting in a syntax similar to `graphicx`.

### 2.2 Image Handling

To facilitate the handling of `tikz` images, this package implements a new environment called `scalable-tikz` that wraps the `tikzpicture` environment in an `adjustbox` environment, so the same syntax can be used as in `graphicx`.

## 3. Miscellaneous

The template defines some other helper functions:

+ `\Re` and `\Im` are redefined so that they are written using `\operatorname` from `amsmath`, so that they share the same font as the main text.
+ `\vect{expression}` formats mathematical vectors with a common style: using `\boldmath`.
+ `\citesources{description}{url}` styles references in a similar style: small text in a non intrusive gray color.
+ `\highlight{text}` highlights text similar to a yellow marker.
