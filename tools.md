# Tools

- [Tools](#tools)
  - [Visual Studio Code](#visual-studio-code)
    - [Navigating files](#navigating-files)
    - [Quickly opening a file](#quickly-opening-a-file)
    - [Saving your changes](#saving-your-changes)
    - [Searching in files](#searching-in-files)
  - [Visual Studio Code extensions](#visual-studio-code-extensions)
    - [Extension updates](#extension-updates)
    - [Code Spell Checker](#code-spell-checker)
      - [Keyboard shortcuts](#keyboard-shortcuts)
      - [Total number of spelling errors in a file](#total-number-of-spelling-errors-in-a-file)
      - [Getting a list of misspelled words](#getting-a-list-of-misspelled-words)
      - [Spelling error marking on scroll bar](#spelling-error-marking-on-scroll-bar)
      - [Custom dictionaries](#custom-dictionaries)
    - [Swedenborg Concordance Language](#swedenborg-concordance-language)
      - [Highlighting is not part of the text](#highlighting-is-not-part-of-the-text)
      - [The syntax highlighting is not perfect](#the-syntax-highlighting-is-not-perfect)
      - [Rule used to determine if reference is malformed](#rule-used-to-determine-if-reference-is-malformed)
    - [Edit csv](#edit-csv)
    - [vscode-pdf](#vscode-pdf)
  - [GitHub Desktop](#github-desktop)

The tools used for cleaning up the concordance files are discussed here.

## Visual Studio Code

Although Visual Studio Code was developed for software development, it's being repurposed here to help editing the plain text concordance files.

### Navigating files

On the vertical activity bar on the left is the Explorer view icon.

![](images/vscode-explorer-icon.png)

You can use this view to navigate the files in the repository.

### Quickly opening a file

If you already know the name of the file you want to open, you can quickly open it by entering a portion of the name of the file in the Command Center. The Command Center can be found at the top center of the application: 

![](images/vscode-command-center.png)

If you know, for example, you want to open `docs\editing.md`, you can simply start typing `edit` in the Command Center from which you can select `editing.md`.

![](images/vscode-file-search.png)

### Saving your changes

To save changes you've made, you can select menu item File -> Save (short key `Ctrl` + `S`).

Alternatively, you can enable auto save so that your edits are automatically saved. To enable this select menu item File -> Auto Save.

### Searching in files

- To search in the file currently being viewed, go to menu item Edit -> Find (shortcut key `Ctrl` + `F`)
- To search across all the files in the repository, go to menu item Edit -> Find in Files (shortcut key `Ctrl` + `Shift` + `F`)

## Visual Studio Code extensions

The Visual Studio Code extensions discussed here aid in editing the concordance files.

### Extension updates

You may see a number on the extensions icon:

![](images/vscode-extension-update-icon.png)

This indicates the number of extensions that are available for update.

You can click the extensions icon and then click the "Reload Required" link to activate the update:

![](images/vscode-extension-reload.png)

Likewise, if an extension is available but Visual Studio Code hasn't yet indicated so, on the icon you can click the extension icon and click on the top right menu (•••) and click "Check for Extension Updates".

It's a good idea to apply these updates (particularly for the Swedenborg Concordance Language extension) to get the latest bug fixes and enhancements.

### Code Spell Checker

The Code Spell Checker extension allows us to have custom spelling dictionary files. Words considered misspelled have a blue squiggly line under them:

![](images/spelling-error-marking.png)

#### Keyboard shortcuts

The following keyboard shortcuts can be used to speed up spell checking:

| Shortcut       | Action                        |
| -------------- | ----------------------------- |
| `F8`           | Go to next spelling error     |
| `Shift` + `F8` | Go to previous spelling error |
| `Ctrl` + `.`   | Quick fix spelling error      |

#### Total number of spelling errors in a file

The total number of spelling errors for the file being edited can be found on the bottom status bar before the word Spell:

![](images/spelling-error-count-status-bar.png)

_Note: For performance reasons Visual Studio Code limits the number of squiggly underlining markings in a file to the first 500 errors._

#### Getting a list of misspelled words

Select the Visual Studio Code menu item View -> Problems to see a list of all the problems indicated in the files opened. Alternatively, you can click on the errors indicator on the left side of the status bar to bring up the list
![](images/errors-status-bar.png):

![](images/spelling-errors-listing.png)

This can be helpful for verifying there are no spelling errors up to the line number you're currently on by checking the first line number that shows up for your file (line 6 in the example above).

Tip: You can right-click on a word in the problems list to bring up the quick fix options for the word.

#### Spelling error marking on scroll bar

Each blue marking on the scrollbar points to a region in the file where there's a spelling error. This provides another indicator of where there are misspellings.

![](images/spelling-error-markings-on-scroll-bar.png)

#### Custom dictionaries

See [here](../.dictionaries/README.md) for a list of the custom dictionaries that we use. These dictionaries are included in the files in this repository. It's possible to add a word to a dictionary when correcting a spelling error. For example, below shows adding the word `persuadedly` to the dictionary of English words used by Swedenborg translators not normally found in modern dictionaries:

![](images/spelling-dictionary-addition.png)

### Swedenborg Concordance Language

To help you with the cleanup, the Swedenborg Concordance Language extension parses the file and attempts to highlight what the elements are in the file by doing the following:

- The English phrase in principal phrase lines are in bold.
- References to works by Swedenborg are in bold and colored.
- Books of the Bible (and optionally followed by chapter verse) are colored.
- Characters considered invalid are colored red.

#### Highlighting is not part of the text

It is important to note that the files are just plain text files without any formatting applied. The highlighting is done by the extension on the fly based on what's currently visible.

**This means that whether highlighting is on, the underlying plain text does not change.**

| Highlighting on | Highlighting off |
| -- | -- |
|![](images/text-with-highlighting-on.png) | ![](images/text-with-highlighting-off.png) |

#### The syntax highlighting is not perfect

The syntax highlighting attempts to apply certain pattern rules to determine, for example, what's a principle phrase line and what's a context reference. It may miss a rule, or as construct used by Potts hasn't yet been considered.

The important thing is to try to be as consistent with Potts as possible (excluding the conversions discussed below).

#### Rule used to determine if reference is malformed

The rule used by the language extension to determine if a reference to a work by Swedenborg is malformed is the [regular expression](https://en.wikipedia.org/wiki/Regular_expression) given below.

```
@(?!(--|(\d+(-\d+)?)|(5M|9Q|AC|AE|AR|Ath|BE|CL|CanonsNC|Char|ConvAng|Coro|DFaith|DLW|DLife|DLord|DLove|DMin|DP|DSS|DWis|DeConj|DeConsum|DeDeoSalv|DeDomino|DeInfluxus|DeJust|DeMiraculis|DeVerbo|Dicta Probantia|Docu|EU|EccHist|HH|HistCrea|ISB|Inv|LJCont|LJPost|LJ|Letters|NJHD|PP|SE|SciaDoc|TCR|Adversaria|WHApp|WH) (\d+(-\d+)?))(\[(\d+|end|half)\])?(\([a-z]{1,2}\))?( |\.|,)).*? 
```
 It's actually possible to search using this expression directly in Visual Studio Code with regular expressions enabled. This can be helpful to quickly verify there are no malformed expressions instead of manually scanning the text for invalid markings.

### Edit csv

CSV (comma separated variable) files are similar to spreadsheet files (in fact they can be opened as spreadsheets in software such as Excel) but they are in plain text.

The Edit csv extension allows for CSV files to be edited in tabular form, making it much easier to see what column is what. To see the content in tabular form, Selecting the "Edit csv" link near the tab of the CSV file

![](images/edit-csv-enable.png)

results in the data being shown in tabular form:

![](images/edit-csv-view.png)

### vscode-pdf

The vscode-pdf extension allows PDF files to be viewed directly in Visual Studio Code. Of course, if you have a preferred PDF viewer you can use that as well too.

## GitHub Desktop

See [Conflict Handling](conflict-handling.md) for handling file conflicts when pulling.
