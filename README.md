# The DISMTools Language Repository

This is the language file repository for DISMTools 0.8.2 and later. Use this repository to make changes to existing language translations, or to provide new translations.

## Working on a new language translation

To work on a new language for DISMTools, follow these guides:

1. Make a fork of this repository and clone it
2. Copy the base `en-US.ini` file into a new file named after **supported language codes**
3. Work on translations while respecting existing syntax

When beginning work on your language file, you must update the `[LanguageFileInformation]` section on the top of the file to identify the language file among other language files:

- `LanguageAuthor` specifies who created the language file. If you've contributed to an existing language, add yourself to the list of authors. Authors are comma-separated
- `LanguageCode` is the language code that the DISMTools localization system will look for. It must be the same as the file name, which must follow LCID Language Tag conventions
- `LanguageName` is the name of the language that will appear in the language picker from Options -> Personalization, or from the DISMTools Initial Setup Wizard (ISW) when running the application for the first time

### Supported language codes

You should name your file using the language code to respect naming conventions with existing INI files. Supported language codes are those from the [*Windows Language Code Identifier (LCID) Reference*](https://winprotocoldoc.z19.web.core.windows.net/MS-LCID/%5bMS-LCID%5d.pdf), Release 7 and later. Language codes appear on pages 31 and later of the LCID reference PDF file.

In some cases, LCID values are supported on older Releases of the LCID spec. These are also supported:

- Release A  -- Windows NT 3.51 and later
- Release B  -- Windows NT 4.0 and later
- Release C  -- Windows 2000 and later
- Release D  -- Windows XP/2003 and later
- Release E1 -- Windows XP SP2 ELKv1/2003/Vista/2008 and later
- Release E2 -- Windows XP SP2 ELKv2/2003/Vista/2008 and later
- Release V  -- Windows Vista/Server 2008 and later

Examples of naming conventions:

| Language | LCID Language Tag |
|:--------:|:----:|
| English (US) | `en-US` |
| Spanish (Spanish) | `es-ES` |
| Chinese (Simplified) | `zh-CN` |

Find the **language tag** for your desired language in the PDF file mentioned above.

### Formatting Syntax

Leverage the following Formatting Syntax to provide dynamism to translation values. You should respect existing formatting syntax in the base en-US file:

- `{0}`, `{1}`, `{2}`... -- for formatted strings, these will be replaced by values stored in variables or returned by expressions
- `{quot;}` -- displays a quote
- `{crlf;}` -- displays a newline
- `{lbrace;}`, `{rbrace;}` -- displays the opening and closing curly braces, `{` and `}`, respectively
- `{space;}` -- displays a space character

## Testing your language file

When working on a language file, you must test it from DISMTools. To do this, copy your language file to the `bin\language` directory of your DISMTools copy. Restart the program if it is already open. Then, go to Tools -> Options -> Personalization and set your language from the language picker.

Next, test either the parts you have worked on (if you are making modifications to an existing translation) or the entirety of the program (if you are creating a new language file or are making major changes to an existing file).

The DISMTools Localization Engine can detect syntax errors. If it detects a syntax error, an exception will be thrown featuring the following information:

- Language Code
- Language File
- Section/Key Reference
- Error and missing entry count
- Unrecognized entry count
- Error reasons

Use this information to fix errors with language files. After you've finished the language file, create the pull request.
