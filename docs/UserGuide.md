---
layout: page
title: User Guide
---

AddressBook Level 3 (AB3) is a **desktop app for managing contacts, optimized for use via a Command Line Interface** (CLI) while still having the benefits of a Graphical User Interface (GUI). If you can type fast, AB3 can get your contact management tasks done faster than traditional GUI apps.

* Table of Contents
{:toc}

--------------------------------------------------------------------------------------------------------------------

## Quick start

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `addressbook.jar` from [here](https://github.com/se-edu/addressbook-level3/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your AddressBook.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:


| Command   | Format                                   |
| --------- | ---------------------------------------- |
| `help`    | `help`                                   |
| `add`     | `add n/NAME [p/PHONE_NUMBER][e/EMAIL] [a/ADDRESS][c/CLASS_NAME...]` |
| `edit`    | `edit INDEX [n/NAME][p/PHONE_NUMBER] [e/EMAIL][a/ADDRESS] [c/CLASS_NAME...]` |
| `delete`  | `delete INDEX`                           |
| `find`    | `find KEYWORD [MORE_KEYWORDS...]`        |
| `list`    | `list`                                   |
| `tagA`    | `addc c/TAG_NAME`                      |
| `tagD` | `deletec c/TAG_NAME`                   |
| `assign`  | `assign INDEX... c/CLASS_NAME`           |
| `listT`   | `listT`                                  |
| `exit`    | `exit`                                   |
| `tagsearch`| `tagsearch t/TAGS`                     |

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `p/12341234 p/56785678`, only `p/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### Viewing help : `help`

Shows a message explaning how to access the help page.

![help message](images/helpMessage.png)

Format: `help`


### Adding a person: `add`

Adds a person to the address book.

Format: `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS [t/TAG]…​`

<div markdown="span" class="alert alert-primary">:bulb: **Tip:**
A person can have any number of tags (including 0)
</div>

Examples:
* `add n/John Doe p/98765432 e/johnd@example.com a/John street, block 123, #01-01`
* `add n/Betsy Crowe t/friend e/betsycrowe@example.com a/Newgate Prison p/1234567 t/criminal`

### Listing all persons : `list`

Shows a list of all persons in the address book.

Format: `list`

### Editing a person : `edit`

Edits an existing person in the address book.

Format: `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [t/TAG]…​`

* Edits the person at the specified `INDEX`. The index refers to the index number shown in the displayed person list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
* You can remove all the person’s tags by typing `t/` without
    specifying any tags after it.

Examples:
*  `edit 1 p/91234567 e/johndoe@example.com` Edits the phone number and email address of the 1st person to be `91234567` and `johndoe@example.com` respectively.
*  `edit 2 n/Betsy Crower t/` Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

### Locating persons by name: `find`

Finds persons whose names contain any of the given keywords.

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only the name is searched.
* Only full words will be matched e.g. `Han` will not match `Hans`
* Persons matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find John` returns `john` and `John Doe`
* `find alex david` returns `Alex Yeoh`, `David Li`<br>
  ![result for 'find alex david'](images/findAlexDavidResult.png)

### Deleting a person : `delete`

Deletes the specified person from the address book.

Format: `delete INDEX`

* Deletes the person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd person in the address book.
* `find Betsy` followed by `delete 1` deletes the 1st person in the results of the `find` command.

### Clearing all entries : `clear`

Clears all entries from the address book.

Format: `clear`

### Exiting the program : `exit`

Exits the program.

Format: `exit`

### adding a tag to a user: `tagA`

adds a tag to from given user

Format: `tagA`

### deleting a tag to a user: `tagD`

deletes a tag from the given user

Format: `tagD`

### deleting a tag to a user: `listT`

lists all the Tags present

Format: `listT`

### searching users with a specific tag: `tagSearch`

finds users with a specific tag and enters a focus mode with users possessing such tags, enters focus mode

Format: `tagSearch`

## Features Available in Focus Mode

The following commands are only available in **tagSearch mode.**

| Command   | Format                               |
| --------- | ------------------------------------ |
| `list`    | `list`                               |
| `session` | `session s/SESSION_NAME [d/DATE]`    |
| `sessionRes`   | `sessionRes INDEX v/VALUE s/SESSION_NAME` |
| `view`    | `view INDEX s/SESSION_NAME`          |
| `lists`   | `lists`                              |
| `back`    | `back`                               |

### List all students with the tag: `list`

<aside>
ℹ️ Shows a list of all students in the class.

</aside>

Format: `list`

- Note that `list` has different behavior in focus mode and outside focus mode.
- In the focus mode, only students with the tag will be listed.

### Create session: `session`

<aside>
ℹ️ Creates a new session.

</aside>

Format: `session s/SESSION_NAME [d/DATE]`

- Creates a new session with name `SESSION_NAME` on `DATE`. If the `DATE` field is empty, the current date will be used.
- `DATE` field should follow the format `dd-MM-yyyy`

Example:

- `session s/Lab1 d/11-08-2022` will create a session `Lab1` on 11  August 2022.

### Grade session: `session_res`

<aside>
ℹ️ Grades the student for the session.

</aside>

Format: `session_res INDEX v/VALUE s/SESSION_NAME`

- provides a result the student with index `INDEX` on the session `SESSION_NAME` with a result of `VALUE`.

Example:

- `session s/Lab1 d/06-10-2022` followed by `sessionRes 2 v/93 s/Lab1` will give the student at index 2 a result of 93 for the session `Lab1`.

### View session grade of student: `view`

<aside>
ℹ️ View the result for a student on a given session.

</aside>

Format: `view INDEX s/SESSION_NAME`

- View the grade of the student at index `INDEX` for the session `SESSION_NAME`.

Example:

- `session s/Lab1 d/06-10-2022` followed by `grade 2 v/93 s/Lab1` then `view 2 s/Lab1` will return 93, which is the grade of the student at index 2 for the session Lab1.

### List all sessions: `lists`

<aside>
ℹ️ List the sessions that have been created for the class.

</aside>

Format: `lists`

- List the sessions that have been created for the class.

### Exit focus mode: `back`

<aside>
ℹ️ Exits focus mode on a class.

</aside>

Format: `back`


### Saving the data

AddressBook data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the data file

AddressBook data are saved as a JSON file `[JAR file location]/data/addressbook.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, AddressBook will discard all data and start with an empty data file at the next run.
</div>

### Archiving data files `[coming in v2.0]`

_Details coming soon ..._

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous AddressBook home folder.

--------------------------------------------------------------------------------------------------------------------

## Command summary

Action | Format, Examples
--------|------------------
**Add** | `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS [t/TAG]…​` <br> e.g., `add n/James Ho p/22224444 e/jamesho@example.com a/123, Clementi Rd, 1234665 t/friend t/colleague`
**Clear** | `clear`
**Delete** | `delete INDEX`<br> e.g., `delete 3`
**Edit** | `edit INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [a/ADDRESS] [t/TAG]…​`<br> e.g.,`edit 2 n/James Lee e/jameslee@example.com`
**Find** | `find KEYWORD [MORE_KEYWORDS]`<br> e.g., `find James Jake`
**List** | `list`
**Help** | `help`
