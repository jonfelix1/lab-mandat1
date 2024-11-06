# Pentaho Data Integration Setup on macOS (M1/M2)

This tutorial will guide you through setting up **Pentaho Data Integration** (PDI) on macOS (M1/M2).

## Prerequisites
- Ensure **Java** is installed on your machine.

## Steps

1. **Create a Project Folder**
   - Create a folder to store Pentaho Data Integration files:
     ```bash
     mkdir pentaho-data-integration
     cd pentaho-data-integration
     ```

2. **Download Pentaho Developer Edition**
   - Download the latest version of **Pentaho Developer Edition** from the official website:
     [https://pentaho.com/pentaho-developer-edition/](https://pentaho.com/pentaho-developer-edition/)
   - Extract the downloaded file (`pdi-ce-10.2.0.0-222.zip`) into the `pentaho-data-integration` folder.

3. **Navigate to the Data Integration Directory**
   - Change into the data integration directory:
     ```bash
     cd data-integration
     ```

4. **Download the Required SWT Library for macOS (M1/M2)**
   - Download the compatible **SWT library**:
     ```bash
     curl -O https://repo1.maven.org/maven2/org/eclipse/platform/org.eclipse.swt.cocoa.macosx.aarch64/3.127.0/org.eclipse.swt.cocoa.macosx.aarch64-3.127.0.jar
     ```

5. **Replace Existing SWT Libraries**
   - Remove the default SWT libraries in the following folders:
     ```bash
     rm libswt/osx64/swt.jar
     rm libswt/osx64_aarch/swt.jar
     ```
   - Copy the downloaded SWT library to both folders:
     ```bash
     cp org.eclipse.swt.cocoa.macosx.aarch64-3.127.0.jar libswt/osx64/
     cp org.eclipse.swt.cocoa.macosx.aarch64-3.127.0.jar libswt/osx64_aarch/
     ```

6. **Extract the `.jnilib` Files**
   - Unzip the **SWT jar file** to access the required `.jnilib` files:
     ```bash
     unzip org.eclipse.swt.cocoa.macosx.aarch64-3.127.0.jar -d swt-extracted
     ```
   - Copy the `.jnilib` files to the **Java library path**:
     ```bash
     cp swt-extracted/*.jnilib ~/.swt/lib/macosx/aarch64/
     ```

7. (Optional, only run on step 6 error)**Create the Directory if Necessary**
   - If you encounter an error and have not previously run any Java applications, create the directory with:
     ```bash
     mkdir -p ~/.swt/lib/macosx/aarch64/
     ```

8. **Run Pentaho Data Integration**
   - Launch the application by running:
     ```bash
     ./spoon.sh
     ```

## Notes
- This setup is specifically tailored for macOS running on M1/M2 chips.
- If you encounter any issues, ensure Java is installed correctly and revisit the SWT library steps.

