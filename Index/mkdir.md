## mkdir command

The `mkdir` command in Windows Command Prompt (cmd) is used to create directories (folders). 


1. **Create a Single Directory:**
   - **Description:** Creates a single directory.
   - **Command:**
     ```cmd
     mkdir FolderName
     ```


2. **Create Multiple Directories:**
   - **Description:** Creates multiple directories at once.
   - **Command:**
     ```cmd
     mkdir Folder1 Folder2 Folder3
     ```

3. **Create a Directory with Spaces:**
   - **Description:** Creates a directory with spaces in its name. Use quotes around the directory name.
   - **Command:**
     ```cmd
     mkdir "Folder With Spaces"
     ```


4. **Create Nested Directories:**
   - **Description:** Creates nested directories in one command.
   - **Command:**
     ```cmd
     mkdir Parent\Child\Grandchild
     ```



5. **Creating Directories and Files Together (Using `&&`):**
   - **Description:** Creates directories and files in a single command line using the `&&` operator.
   - **Command:**
     ```cmd
     mkdir Folder1 Folder2 && (echo File content > Folder1\file1.txt) && (echo File content > Folder2\file2.txt)
     ```


6. **Creating directories and multiple files with in-folder together (using `&&`):**
   - **Description:** Creates directories and files in a single command line using the `&&` operator.
   - **Command:**
     ```cmd
     mkdir Folder1 Folder2 && (echo File content > Folder1\file1.txt) && (echo File content > Folder1\file2.txt) && (echo File content > Folder2\file1.txt) && (echo File content > Folder2\file2.txt)
     ```


7. **Create Directories with Conditional Logic:**
   - **Description:** Conditionally create a directory only if it doesn't already exist.
   - **Command:**
     ```cmd
     if not exist "FolderName" mkdir "FolderName"
     ```


By using these commands, you can efficiently create directories and structure your files and folders as needed in the Windows Command Prompt.
