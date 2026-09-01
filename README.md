# NX-Seed-Finder-and-Extractor
https://raw.githubusercontent.com/yyoossk/NX-Seed-Finder-and-Extractor/refs/heads/main/screen.bmp
A Windows utility for detecting MArchive seeds from `main_uncompressed` files and extracting `alldata.psb.m` / `alldata.bin` using `MArchiveBatchTool.exe`.

NX Seed Finder and Extractor is designed for supported NS titles that use MArchive-based data.

It can automatically analyze `main_uncompressed`, detect the seed when possible, and assist with archive extraction through a simple graphical interface.

---

## Features

* Automatically detects MArchive seeds from `main_uncompressed`
* Displays the detected seed in a selectable and copyable field
* Supports titles that do not originally use a seed
* Automatically switches to No Seed extraction mode when appropriate
* Extracts `alldata.psb.m` and `alldata.bin` using `MArchiveBatchTool.exe`
* Lets you choose a custom extraction destination
* Shows extraction progress with a clear green progress meter
* Displays `MArchiveBatchTool.exe` output in real time
* Supports drag and drop for files and folders
* Works even when files are stored in different folders or drives
* Automatically opens the extracted folder after completion
* Automatically selects the UI language based on the Windows system language
* Allows manual language switching
* High-DPI-aware Windows interface
* Available in both 32-bit and 64-bit builds
* Uses an embedded application icon
* Does not require `MArchiveBatchTool.exe` when you only want to detect the seed

---

## Downloads

Download the latest release from the GitHub **Releases** page.

Recommended files:

* `NX Seed Finder and Extractor.exe` — 32-bit version
* `NX Seed Finder and Extractor x64.exe` — 64-bit version

### Which Version Should I Use?

For most modern Windows PCs, use the **64-bit version**.

The 32-bit version is also available and can run on most 64-bit Windows systems through WOW64.

---

## Screenshot

Add a screenshot of the application here.

```markdown
![NX Seed Finder and Extractor](images/screenshot.png)
```

Suggested screenshots:

* Main window
* Seed detection result
* No Seed result
* Extraction in progress
* Real-time log output
* Language selection menu

---

## Requirements

### For Seed Detection

Only the following file is required:

```text
main_uncompressed
```

> If you only want to know the seed, the `main_uncompressed` file is all you need.

`main_uncompressed` is obtained by decrypting and extracting the Nintendo Switch `main` file using a tool such as hactool.

### For Archive Extraction

The following are required:

```text
main_uncompressed
alldata.bin
alldata.psb.m
MArchiveBatchTool.exe
```

You must also select an extraction destination folder.

---

## Finding the Seed

1. Start NX Seed Finder and Extractor.
2. Select or drag and drop `main_uncompressed`.
3. Click **Find Seed**.
4. Wait for the analysis to finish.
5. The detected seed will appear in the result field.
6. Copy the seed if needed.

The seed field can be selected normally and supports standard clipboard operations.

---

## When "No Seed" Is Displayed

The application may return:

```text
No Seed
```

This can mean one of two things:

* The title originally does not use a seed.
* The title uses a seed that cannot currently be detected by this application.

> A **No Seed** result does not always guarantee that the original title has no seed.

If the title genuinely does not use a seed, archive extraction may still work.

When **No Seed** is detected, the application automatically uses the dedicated No Seed extraction mode.

---

## Archive Extraction

To extract the archive:

1. Select `main_uncompressed`.
2. Click **Find Seed**.
3. Select the folder containing `MArchiveBatchTool.exe`.
4. Select `alldata.bin`.
5. Select `alldata.psb.m`.
6. Select the extraction destination.
7. Click **Extract**.
8. Monitor the progress meter and real-time log.
9. When extraction finishes, the extracted folder opens automatically.

---

## Normal Seed Extraction

When a normal seed is detected, the application performs an operation equivalent to:

```text
MArchiveBatchTool.exe fullunpack --keep alldata.psb.m zlib <SEED> 64
```

Example:

```text
MArchiveBatchTool.exe fullunpack --keep alldata.psb.m zlib 25G/xpvTbsb+6 64
```

The application passes the seed directly to `MArchiveBatchTool.exe`.

You do not need to enter the command manually.

---

## No Seed Extraction

When the result is **No Seed**, the application automatically uses:

```text
MArchiveBatchTool.exe fullunpack --keep alldata.psb.m zlib "Illegal function call" 92
```

This mode is intended for titles that originally do not use a normal seed.

You do not need to enter this command manually.

---

## Extraction Destination

You can choose any destination folder.

After successful extraction, the following directory is created inside the selected destination:

```text
alldata.psb.m_extracted
```

The folder is automatically opened in Windows File Explorer when extraction completes.

---

## Drag and Drop

NX Seed Finder and Extractor supports drag and drop.

You can drag the following directly onto their corresponding fields:

* `main_uncompressed`
* `alldata.bin`
* `alldata.psb.m`
* MArchiveBatchTool folder
* Extraction destination folder

The files do not need to be in the same directory.

They can also be located on completely different drives.

The application handles the necessary paths automatically.

---

## Progress Information

During extraction, a green progress meter fills from left to right.

The application also displays the current processing stage.

Typical stages include:

* Preparing
* Validating input files
* Creating the temporary workspace
* Copying archive files
* Starting MArchiveBatchTool
* Extracting archive data
* Checking extraction results
* Moving extracted files
* Cleaning up temporary data
* Completed

The progress meter intentionally does not display a percentage number inside the bar.

---

## Real-Time Log

Output from `MArchiveBatchTool.exe` is displayed directly inside the application.

Both standard output and error output are shown in real time.

This makes it easier to understand what the extraction process is doing and diagnose problems.

Use **Clear Log** to remove the currently displayed log.

---

## Language Support

The application automatically selects its display language based on the Windows system language.

You can manually change the language at any time from the **Language** menu.

Currently supported languages:

* Japanese
* English
* Simplified Chinese
* Traditional Chinese
* Korean
* German
* French
* Spanish
* Italian
* Portuguese
* Russian

The selected language is saved and restored the next time the application starts.

---

## High-DPI Support

NX Seed Finder and Extractor is designed to work correctly with common Windows display scaling settings.

Examples include:

* 100%
* 125%
* 150%
* 175%
* 200%

You should not need to manually change the application's Windows High DPI compatibility settings.

---

## File Locations

The following files may all be stored in different directories:

```text
main_uncompressed
alldata.bin
alldata.psb.m
MArchiveBatchTool.exe
```

The extraction destination may also be located on another drive.

The application creates and manages the required temporary workspace automatically.

---

## Basic Workflow

### Seed Detection Only

```text
main_uncompressed
        ↓
Find Seed
        ↓
Seed Result
```

Only `main_uncompressed` is required.

### Seed Detection and Extraction

```text
main_uncompressed
        ↓
Find Seed
        ↓
Detected Seed / No Seed
        ↓
Select MArchiveBatchTool folder
        ↓
Select alldata.bin
        ↓
Select alldata.psb.m
        ↓
Select extraction destination
        ↓
Extract
        ↓
alldata.psb.m_extracted
```

---

## Troubleshooting

### The Application Displays "No Seed"

This may mean the title genuinely does not use a seed.

It may also mean the current detection algorithm does not support that title.

Try extraction using the automatically selected No Seed mode.

---

### Seed Detection Works but Extraction Fails

Check that:

* `MArchiveBatchTool.exe` is present in the selected folder
* `alldata.bin` is correct
* `alldata.psb.m` is correct
* Both archive files belong to the same title/version
* The extraction destination is writable
* There is enough free disk space

Check the real-time log for additional information.

---

### MArchiveBatchTool Cannot Be Found

Select the **folder containing**:

```text
MArchiveBatchTool.exe
```

Do not select an unrelated folder.

You can also drag and drop the folder into the application.

---

### The Extracted Folder Already Exists

The application includes safeguards for an existing:

```text
alldata.psb.m_extracted
```

directory.

Existing extraction data is handled carefully to reduce the chance of accidental data loss if a new extraction fails.

---

### Drag and Drop Does Not Select the Expected Item

Make sure the item is dropped onto the corresponding input field.

For example:

* Drop `main_uncompressed` onto the main file field.
* Drop `alldata.bin` onto the `alldata.bin` field.
* Drop `alldata.psb.m` onto the `alldata.psb.m` field.

---

## Frequently Asked Questions

### Do I Need MArchiveBatchTool Just to Find the Seed?

No.

If you only want to detect the seed, you only need:

```text
main_uncompressed
```

---

### Do All Titles Have a Seed?

No.

Some titles may not use a normal seed.

The application can display **No Seed** for these titles.

However, **No Seed** may also mean that the current detection method cannot identify the seed.

---

### Can the Files Be on Different Drives?

Yes.

For example:

```text
C:\Tools\MArchiveBatchTool.exe
D:\Game\main_uncompressed
E:\Archive\alldata.bin
E:\Archive\alldata.psb.m
F:\Extracted\
```

is supported.

---

### Can I Copy the Detected Seed?

Yes.

The detected seed is displayed in a selectable text field and can be copied normally.

---

### Does the Application Modify main_uncompressed?

No.

`main_uncompressed` is analyzed as an input file.

---

### Does the Application Include MArchiveBatchTool?

No.

`MArchiveBatchTool.exe` is an external tool and must be provided separately.

---

## Seed Detection Method

NX Seed Finder and Extractor does not simply search for a hard-coded seed string.

The detector analyzes characteristics of the executable data, including known MArchive initialization patterns and ARM64 string references.

The detection system uses multiple conditions to reduce false positives.

Because titles may use different implementations, detection is not guaranteed for every title.

---

## Safety and Error Handling

The application includes checks intended to reduce common extraction problems.

Examples include:

* Input file validation
* Process execution checks
* Temporary workspace handling
* Extraction result validation
* Existing output folder protection
* Process exit-code checking
* Real-time error logging
* Prevention of overlapping seed detection and extraction operations

---

## External Tools

Archive extraction requires:

### MArchiveBatchTool

`MArchiveBatchTool.exe` must be obtained separately.

NX Seed Finder and Extractor only calls the executable selected by the user.

### hactool

A tool such as hactool may be used to obtain `main_uncompressed` from a legally obtained Nintendo Switch `main` file.

hactool is not required by NX Seed Finder and Extractor itself once `main_uncompressed` has already been created.

---

## Known Limitations

* Seed detection may not work with every MArchive implementation.
* A **No Seed** result can mean either that no seed exists or that the current detector cannot identify it.
* Extraction compatibility depends on `MArchiveBatchTool.exe`.
* New or significantly different MArchive implementations may require future detector updates.

---

## Disclaimer

This project is intended for research, interoperability, preservation, and analysis of files that you legally own or are authorized to access.

No copyrighted game data is included with this project.

Users are responsible for ensuring that their use of the software complies with applicable laws and licenses.

---

## Credits

NX Seed Finder and Extractor uses `MArchiveBatchTool.exe` as an external extraction tool when archive extraction is requested.

Thanks to the developers and researchers whose work has contributed to understanding MArchive formats.
