# File Permissions Management in Linux

## Project Description

The research team at the organization needed to update file permissions for certain files and directories within the `projects` directory. The existing permissions did not reflect the level of authorization that should have been granted. Checking and updating these permissions helps keep the system secure. The following tasks were performed to complete this.

## 1. Check File and Directory Details

The `ls -la` command was used to display a detailed listing of the directory's contents, including hidden files.

![Checking file and directory permissions](linux-file-permissions-images/01-check-permissions.png)

The output shows one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files. The 10-character string in the first column of each row represents the permissions set on that file or directory.

## 2. The Permissions String, Explained

The 10-character permissions string breaks down as follows:

| Position | Meaning |
|---|---|
| 1st character | File type — `d` for directory, `-` for a regular file |
| 2nd–4th characters | Read (`r`), write (`w`), execute (`x`) permissions for the **user** (owner). A `-` means that permission is not granted. |
| 5th–7th characters | Read, write, execute permissions for the **group**. |
| 8th–10th characters | Read, write, execute permissions for **other** (all other users on the system). |

**Example:** `project_t.txt` has the permission string `-rw-rw-r--`.
- The leading `-` means it's a regular file, not a directory.
- Characters 2, 5, and 8 are all `r` — user, group, and other all have read permissions.
- Characters 3 and 6 are `w` — only user and group have write permissions.
- No one has execute permissions.

## 3. Change File Permissions

The organization determined that **other** shouldn't have write access to any files. Based on the permissions checked earlier, `project_k.txt` needed its write access removed for other.

![Removing write access for 'other' on project_k.txt](linux-file-permissions-images/02-change-project_k-permissions.png)

The `chmod` command changes permissions on files and directories — the first argument specifies what to change, the second specifies the target file. Here, `chmod o-w project_k.txt` removed write permissions from other. `ls -la` was then used again to confirm the update.

## 4. Change Permissions on a Hidden File

The research team had recently archived `project_x.txt` and wanted no one to have write access, while user and group should retain read access.

![Updating permissions on the hidden file .project_x.txt](linux-file-permissions-images/03-change-hidden-file-permissions.png)

`.project_x.txt` is a hidden file, identifiable by the leading period in its name. The command `chmod u-w,g-w,g+r .project_x.txt` removed write permissions from both the user and group, and added read permissions for the group.

## 5. Change Directory Permissions

The organization wanted only the `researcher2` user to have access to the `drafts` directory and its contents — meaning no one other than `researcher2` should have execute permissions.

![Removing group execute permission on the drafts directory](linux-file-permissions-images/04-change-directory-permissions.png)

The group previously had execute permissions on `drafts`, so `chmod g-x drafts` was used to remove them. The `researcher2` user already had execute permissions, so no change was needed there.

## Summary

Multiple permissions were changed to match the level of authorization the organization required for files and directories in the `projects` directory. The process began with `ls -la` to check existing permissions, which informed each subsequent decision. The `chmod` command was then used several times to update permissions on individual files and on the `drafts` directory.
