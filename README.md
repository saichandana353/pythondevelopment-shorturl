# python designated location files
import shutil
import os
import datetime

def backup_files(source_path, destination_path):
    # Ensure source path exists
    if not os.path.exists(source_path):
        print(f"Source path '{source_path}' does not exist.")
        return

    # Create a timestamp for the backup folder
    timestamp = datetime.datetime.now().strftime("%Y%m%d%H%M%S")
    
    # Construct the destination path with a timestamp
    backup_folder = f"{destination_path}/backup_{timestamp}"
    
    try:
        # Copy the entire directory to the backup location
        shutil.copytree(source_path, backup_folder)
        print(f"Backup successful. Files copied to '{backup_folder}'.")
    except Exception as e:
        print(f"Backup failed. Error: {e}")

# Example usage
source_path = '/path/to/source'
destination_path = '/path/to/backup'

backup_files(source_path, destination_path)

