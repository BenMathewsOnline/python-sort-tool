import os
import shutil

def sort_files_by_extension(directory):
    for filename in os.listdir(directory):
        # Skip directories and only process files
        if os.path.isfile(os.path.join(directory, filename)):
            file_extension = os.path.splitext(filename)[1].lower()

            # Create a folder for each file extension if it doesn't exist
            extension_folder = os.path.join(directory, file_extension)
            if not os.path.exists(extension_folder):
                os.makedirs(extension_folder)

            # Move the file to its corresponding folder
            shutil.move(os.path.join(directory, filename), os.path.join(extension_folder, filename))

def sort_files_alphabetically(directory):
    for foldername in os.listdir(directory):
        folder_path = os.path.join(directory, foldername)

        # Skip files and only process folders
        if os.path.isdir(folder_path):
            files = sorted(os.listdir(folder_path))
            for index, filename in enumerate(files, start=1):
                old_path = os.path.join(folder_path, filename)
                new_path = os.path.join(folder_path, f"{index:03}_{filename}")
                os.rename(old_path, new_path)

if __name__ == "__main__":
    base_directory = os.getcwd()

    # Sort files by their file extension
    sort_files_by_extension(base_directory)

    # Sort files alphabetically within each folder
    sort_files_alphabetically(base_directory)

python file_sorting_automation.py


5. The script will sort the files in the directory by their file extension and then sort them alphabetically within each folder.

## Notes

- This script will only process files in the directory where it's located. It won't process files in subdirectories.
- The script will create folders based on the file extensions and move the files into those folders.
- The script will sort the files alphabetically within each folder and prepend a 3-digit index to the file names to maintain the alphabetical order.

## License

This project is released under the MIT License. See the `LICENSE` file for more information.
