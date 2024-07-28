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
     mkdir Folder1 Folder2 && (echo ^add data^ > Folder1\file1.txt) && (echo ^add data^ > Folder2\file2.txt)
     ```


6. **Creating directories and multiple files with in-folder together (using `&&`):**
   - **Description:** Creates directories and  multiple files with in-folder together in a single command line using the `&&` operator.
   - **Command:**
     ```cmd
     mkdir Folder1 Folder2 && (echo ^add data^ > Folder1\file1.txt) && (echo ^add data^ > Folder1\file2.txt) && (echo ^add data^ > Folder2\file1.txt) && (echo ^add data^ > Folder2\file2.txt)
     ```
   - **PHP folders/files Command:**
     ```cmd
     mkdir config public src templates assets\css  assets\js && (echo ^add data^ > config\database.php) && (echo ^add data^ > public\index.php) && (echo ^add data^ > public\login.php) && (echo ^add data^ > public\dashboard.php) && (echo ^add data^ > src\auth.php) && (echo ^add data^ > src\user.php) && (echo ^add data^ > templates\header.php) && (echo ^add data^ > templates\footer.php)&& (echo ^add data^ > templates\login_form.php)&& (echo ^add data^ > templates\dashboard.php) && (echo ^add data^ > assets\css\style.css) && (echo ^add data^ > assets\js\script.js)
     ```


7. **Create Directories with Conditional Logic:**
   - **Description:** Conditionally create a directory only if it doesn't already exist.
   - **Command:**
     ```cmd
     if not exist "FolderName" mkdir "FolderName"
     ```


By using these commands, you can efficiently create directories and structure your files and folders as needed in the Windows Command Prompt.
