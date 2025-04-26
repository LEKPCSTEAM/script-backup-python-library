# Python Package Backup with `.whl` Files

This guide explains how to back up Python package dependencies using `.whl` (wheel) files from your `requirements.txt`. These steps allow you to save the necessary package files and install them later without needing an internet connection.

## Steps to Backup Python Packages

### 1. Create `requirements.txt`

If you don't already have a `requirements.txt` file, create one by freezing your current environment's dependencies:

```bash
pip freeze > requirements.txt
```
This will generate a requirements.txt file with all the currently installed packages and their versions.

2. Download .whl Files for All Packages
Use the following command to download the .whl files for all the packages listed in requirements.txt:

```bash
mkdir packages
pip download -r requirements.txt -d packages/
```
-r requirements.txt: Specifies the requirements.txt file containing the list of dependencies.
-d packages/: Downloads all .whl files into the packages/ directory.

3. Verify the Downloaded .whl Files
After running the command, you should see a folder called packages/ containing all the .whl files of the packages listed in requirements.txt.

4. Install Packages from .whl Files
If you want to install the packages from the downloaded .whl files without an internet connection, you can use the following command:

```bash
pip install --no-index --find-links=packages/ -r requirements.txt
```
# --no-index: Prevents pip from searching the PyPI index.

--find-links=packages/: Tells pip to look for the .whl files in the packages/ directory.
5. Restore Dependencies
To restore the environment in the future, simply repeat the process of downloading the .whl files and installing them from the local files.

Additional Notes
Make sure the Python version and system architecture are compatible with the .whl files you're downloading.

You can distribute the packages/ folder along with your requirements.txt to ensure that all dependencies are available for offline installations.

By following these steps, you'll be able to back up your Python packages as .whl files and install them later without needing an internet connection.
