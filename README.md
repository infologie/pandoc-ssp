# Pandoc-SSP (single-source publishing with Pandoc and Make)

This a template for single-source academic publishing with [Pandoc](https://pandoc.org/). It illustrates how you can use [Make](https://www.gnu.org/software/make/) to automate a complex conversion process.

I ([Arthur Perret](https://www.arthurperret.fr)—hello!) use this to export my PhD dissertation in HTML and PDF from the same collection of text files. If you’re a researcher looking to turn your scientific writing into HTML and PDF from a single source, this template provides directions to do so.

## ⚠️ Disclaimer

**This repository does not work as a self-demonstrating example.** Do not try running `make` directly: since most of the files are empty, the process will inevitably fail. Instead, replace the files with your own.

**This is a small tool, for basic needs.** You may be interested in a more advanced system based on Pandoc, such as [Manubot](https://manubot.org) or [Quarto](https://quarto.org). But if (like me) you usually try out simple tools first, read on.

**If you do not know Make, I encourage you to read a tutorial before using this template.** I made this because I wanted something that would create both HTML like Ivan Stojic’s [Pandoc-SSG](https://github.com/ivanstojic/pandoc-ssg/) and PDF like Abrüpt’s [Gabarit](https://gitlab.com/cestabrupt/gabarit-abrupt). Both use Make to automate Pandoc conversions. After wasting some time trying to merge the two, I decided to make my own Makefile from scratch, which was a more sensible approach. I learned the basics of Make with this excellent tutorial: [Makefile tutorial by example](https://makefiletutorial.com).

## How it works

The idea is simple: Make is used to automate a series of file conversions with Pandoc. Some files are used in each conversion process: text, references, bibliographic style. Others are format-specific: template, metadata.

The Makefile is where the magic happens. There are a few lines you may want to leave as is, the ones that enable the recursive copy of static content (a trick I borrowed from StackOverflow). Everything else can be adapted (I did not bother to use variables for customizable things, like paths… feel free to do your own thing).

As it is written, the Makefile uses the following folders:

- `text`: Markdown files, which you organize any way you want (subdirectories are helpful if you want different Pandoc commands for different groups of files)
- `output`: output folder
- `static`: static folder, for anything that needs to be copied as is in the output (e.g., for the HTML version: CSS, fonts, images…)

The root contains:

- the `Makefile`
- `metadata.yml`: metadata which Pandoc can use to fill the templates
- templates, such as `template.html` and `template.tex`
- `references.bib`: bibliographic data (could be CSL JSON or any other format supported by Pandoc)
- `style.csl`: bibliographic style
- `index.md`: this becomes the `index.html` of the HTML version

I deliberately left the Pandoc options blank and included only empty files (except for the [Makefile](Makefile), obviously). This means **you need to drop in your own files and add Pandoc options yourself**. Check [Pandoc’s User Guide](https://pandoc.org/MANUAL.html) and the [Pandoc templates repository](https://github.com/jgm/pandoc-templates) if you haven’t already.

Here is an example diagram of the conversion process. Your mileage may vary. For instance, you may want to use `metadata.yml` in both conversion processes.

![Example diagram of the conversion process used in this template](https://www.arthurperret.fr/img/pandoc-ssp-condensed.png)

[Click here](https://www.arthurperret.fr/img/pandoc-ssg.pdf) to download a one-page PDF cheatsheet with the diagram, file tree and Makefile.

Again, everything is adaptable.

I hope you find it useful.
