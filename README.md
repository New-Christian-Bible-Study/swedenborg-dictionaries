# Custom Dictionaries for Swedenborg's Works

The dictionary files in the directory are used to help spell check scans of works from Swedenborg.

| File | Content |
|--|--|
| [dictionary-en-swedenborg.txt](./dictionary-en-swedenborg.txt) | English words translated from Swedenborg's Latin not used in modern US English dictionaries |
| [dictionary-works-abbrev.txt](./dictionary-works-abbrev.txt) | Abbreviations used for Swedenborg's works |
| [dictionary-la-swedenborg.txt](./dictionary-la-swedenborg.txt) | Latin words unique to Swedenborg's works |
| [dictionary-la-lewis-short.txt](./dictionary-la-lewis-short.txt) | Latin dictionary provided by Charlton T. Lewis and Charles Short (Oxford 1891) found [here](https://sourceforge.net/projects/scrabble/files/Dictionaries/latin.zip/download) |
| [dictionary-sv.txt](./dictionary-sv.txt) | Swedish words |
| [concordance-words.txt](./concordance-words.txt) | Concordance words (PPEs) |
| [proper-names.txt](./proper-names.txt) | Proper Names |
| [old-style.txt](./old-style.txt) | old style usage (incl. Biblical) |

## Using the dictionaries for spell checking in Visual Studio Code

The Visual Studio Code extension [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) has been found to work well using these dictionary files.

### Setting up the to use the extension

Here's the steps to setup the Code Spell Checker extension in Visual Studio Code in the repository containing the text files related to Swedenborg that will be edited:

#### 1. Install the extension

Click the Install button at [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker).

#### 2. Copy the dictionary files to your repository

In the root directory of your repository create a directory named `.dictionaries` and copy the dictionary files to this directory.

#### 3. Configure the spell checker to use the dictionary files

Create `.vscode/settings.json` with the following content. (If the file already exists, exclude the top and bottom braces.)

```
{
  // The minimum length of a word before checking it against a dictionary.
  "cSpell.minWordLength": 2,

  "cSpell.customDictionaries": {
    "swedenborgEnglish": {
      "name": "Swedenborg English words",
      "path": "${workspaceFolder}/.dictionaries/dictionary-en-swedenborg.txt",
      "scope": "workspace",
      "addWords": true
    },
    "swedenborgWorksAbbrevs": {
      "name": "Swedenborg Works abbreviations",
      "path": "${workspaceFolder}/.dictionaries/dictionary-works-abbrev.txt",
      "scope": "workspace",
      "addWords": false
    },
    "swedenborgLatin": {
      "name": "Swedenborg Latin words",
      "path": "${workspaceFolder}/.dictionaries/dictionary-la-swedenborg.txt",
      "scope": "workspace",
      "addWords": true
    },
    "Swedish": {
      "name": "Swedish dictionary",
      "path": "${workspaceFolder}/.dictionaries/dictionary-sv.txt",
      "scope": "workspace",
      "addWords": true
    },
    "Latin": {
      "name": "Latin dictionary provided by Lewis and Short (do not modify)",
      "path": "${workspaceFolder}/.dictionaries/dictionary-la-lewis-short.txt",
      "scope": "workspace",
      "addWords": false
    },
    "Concordance": {
      "name": "Concordance words (PPEs) (do not modify)",
      "path": "${workspaceFolder}/.dictionaries/dictionary-la-lewis-short.txt",
      "scope": "workspace",
      "addWords": false
    }
  },

  // Add entries to cSpell.enabledFileTypes to enable spell checking for types not recognized by default.
}
```

#### 4. Install any Code Spell Checker language extensions of interest

The **Language Dictionaries** section of [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) lists extensions that can be installed to add support for additional languages. For example, there are Latin and Swedish language extensions available.

### Using the spell checker

### Code Spell Checker

Words considered misspelled have a blue squiggly line under them:

![](images/spelling-error-marking.png)

#### Keyboard shortcuts

The following keyboard shortcuts can be used to speed up spell checking:

| Shortcut       | Action                        |
| -------------- | ----------------------------- |
| `F8`           | Go to next spelling error     |
| `Shift` + `F8` | Go to previous spelling error |
| `Ctrl` + `.`   | Quick fix spelling error      |

#### Getting a list of misspelled words

Select the Visual Studio Code menu item View -> Problems to see a list of all the problems indicated in the files opened. Alternatively, you can click on the errors indicator on the left side of the status bar to bring up the list
![](images/errors-status-bar.png):

![](images/spelling-errors-listing.png)

This can be helpful for verifying there are no spelling errors up to the line number you're currently on by checking the first line number that shows up for your file (line 6 in the example above).

Tip: You can right-click on a word in the problems list to bring up the quick fix options for the word.

#### Spelling error marking on scroll bar

Each blue marking on the scrollbar points to a region in the file where there's a spelling error. This provides another indicator of where there are misspellings.

![](images/spelling-error-markings-on-scroll-bar.png)
