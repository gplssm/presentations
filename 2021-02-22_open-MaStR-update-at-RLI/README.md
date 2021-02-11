Slides for talk about MaStR and open-MaStR at RLI on 22th of February 2021

# Installation

You need to have some Latex packages installed. Linux users may use

```
sudo apt install texlive
sudo apt install texlive-xetex # to use unicode-aware xelatex
sudo apt install texlive-latex-recommended # for latex beamer
sudo apt install texlive-fonts-extra # maybe required for fonts
```

Note: If you don't want to litter your system with the countless fonts from `texlive-fonts-extra` (a full list of the
Ubuntu package can be found [here](https://packages.ubuntu.com/xenial/texlive-fonts-extra)), you can get single
fonts by installing the specific system package. E.g. to install Roboto, use

```
sudo apt install fonts-roboto-hinted
```

## Extra packages for markdown (pandoc)

```
sudo apt install pandoc
```

When using pandoc, it's recommended to use a version >2.0. Ubuntu/Debian user should know that pandoc from official sources might be outdated. Consider to install a [newer version](https://pandoc.org/installing.html).

For using citations with pandoc pandoc-citeproc is required

```
sudo apt install pandoc-citeproc
```

# Build slides (PDF)

Convert `.md` files to beamer PDF slides by


```
pandoc -t beamer --pdf-engine=xelatex -o slides-draft.pdf slides-draft.md
```

Note: If you use **pandoc version <2.0**, replace `--pdf-engine` by `--latex-engine=` to process the Markdown file.

Have a look into `example_slides.md` for details and examples.

