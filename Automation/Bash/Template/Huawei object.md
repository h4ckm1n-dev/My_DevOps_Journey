## Script to download object from a Huawei S3 storage

1. Update the script: Open the script file (`download_folder_contents.sh`) in a text editor.
2. Configure variables: Replace the placeholder values with the appropriate information:
    - `bucket_name`: Replace `'your_bucket_name'` with the name of your S3 bucket.
    - `folder_key`: Replace `'path/to/your/folder/'` with the key of the folder you want to download from the S3 bucket.
    - `local_path`: Replace `'local/directory/to/save/objects/'` with the local directory path where you want to save the downloaded objects.
    - `endpoint_url`: Replace `'your_custom_endpoint_url'` with the custom endpoint URL if applicable.
3. Save the changes: Save the script file after updating the variables.
4. Make the script executable: In a terminal, navigate to the directory where the script is located and run the following command to make it executable:
    ```bash
    chmod +x download_folder_contents.sh
```
    
5. Run the script: Execute the script by running the following command:
    ```bash
    ./download_folder_contents.sh
```
    
6. View the output: The script will start the download process and display the progress. Once completed, it will provide a success message if all objects were downloaded successfully or an error message if there was a problem.
7. Check the downloaded objects: Open the local directory you specified (`local/directory/to/save/objects/`) to verify that the objects from the S3 folder have been downloaded.

That's it! You can now use the script to automatically download all the contents of a folder from your S3 storage using the [[AWS-CLI]].

```bash
#!/bin/bash

################################################################################
# Script: download_folder_contents.sh
#
# Description: This script downloads all the contents of a folder from an S3
#              storage using the AWS CLI.
#
# Usage: ./download_folder_contents.sh
#
# Author: Mayer Julien
# Version: 1.0
################################################################################

bucket_name="your_bucket_name"
folder_key="path/to/your/folder/"
local_path="local/directory/to/save/objects/"
endpoint_url="your_custom_endpoint_url"

# Create the local directory if it doesn't exist
if [ ! -d "$local_path" ]; then
    mkdir -p "$local_path"
fi

aws s3 sync "$bucket_name/$folder_key" "$local_path" --endpoint-url "$endpoint_url"

if [ $? -eq 0 ]; then
    echo "Successfully downloaded all objects from folder '$folder_key' in bucket '$bucket_name'"
else
    echo "Error downloading objects from folder '$folder_key' in bucket '$bucket_name'"
fi

```

  
To upload the contents of a folder to an S3 storage using the AWS CLI, you can use the following script:

```bash
#!/bin/bash

################################################################################
# Script: upload_folder_contents.sh
#
# Description: This script uploads all the contents of a local folder to an S3
#              storage using the AWS CLI.
#
# Usage: ./upload_folder_contents.sh
#
# Author: Mayer Julien
# Version: 1.0
################################################################################

bucket_name="your_bucket_name"
folder_key="path/to/your/folder/"
local_path="local/directory/to/upload/"
endpoint_url="your_custom_endpoint_url"

aws s3 sync "$local_path" "$bucket_name/$folder_key" --endpoint-url "$endpoint_url"

if [ $? -eq 0 ]; then
    echo "Successfully uploaded all objects from folder '$local_path' to '$bucket_name/$folder_key'"
else
    echo "Error uploading objects from folder '$local_path' to '$bucket_name/$folder_key'"
fi

```

Make sure to replace the placeholders with the appropriate values:

- `your_bucket_name`: The name of your S3 bucket.
- `path/to/your/folder/`: The key or path of the folder in your S3 bucket where you want to upload the contents.
- `local/directory/to/upload/`: The local directory path containing the contents you want to upload.
- `your_custom_endpoint_url`: The custom endpoint URL for your S3 storage (if applicable). If you are using the default AWS S3 service, you can omit this or set it to the default endpoint URL.

Save the script to a file, such as `upload_folder_contents.sh`, and make it executable using the command `chmod +x upload_folder_contents.sh`. Then, you can run the script by executing `./upload_folder_contents.sh` in your terminal.

To add checksum verification when uploading the contents of a folder to an S3 storage using the AWS CLI, you can modify the script as follows:
```bash
#!/bin/bash

################################################################################
# Script: upload_folder_contents.sh
#
# Description: This script uploads all the contents of a local folder to an S3
#              storage using the AWS CLI and performs checksum verification.
#
# Usage: ./upload_folder_contents.sh
#
# Author: Mayer Julien
# Version: 1.0
################################################################################

bucket_name="your_bucket_name"
folder_key="path/to/your/folder/"
local_path="local/directory/to/upload/"
endpoint_url="your_custom_endpoint_url"

# Calculate checksum for each file before upload
calculate_checksum() {
  local file_path="$1"
  md5sum "$file_path" | awk '{print $1}'
}

# Verify checksum after upload
verify_checksum() {
  local file_path="$1"
  local expected_checksum="$2"
  local actual_checksum=$(aws s3api head-object --bucket "$bucket_name" --key "$folder_key$file_path" --endpoint-url "$endpoint_url" --query 'ETag' --output text | tr -d '"')
  if [ "$expected_checksum" = "$actual_checksum" ]; then
    echo "Checksum verification passed for file: $file_path"
  else
    echo "Checksum verification failed for file: $file_path"
  fi
}

# Create the local directory if it doesn't exist
if [ ! -d "$local_path" ]; then
    mkdir -p "$local_path"
fi

# Upload the contents of the folder to S3
aws s3 sync "$local_path" "$bucket_name/$folder_key" --endpoint-url "$endpoint_url" --no-progress

# Perform checksum verification for each file
if [ $? -eq 0 ]; then
  while IFS= read -r -d '' file; do
    checksum=$(calculate_checksum "$file")
    verify_checksum "$file" "$checksum"
  done < <(find "$local_path" -type f -print0)
fi

```

In this modified script, I've added two functions: `calculate_checksum` and `verify_checksum`. The `calculate_checksum` function calculates the MD5 checksum for a file, and the `verify_checksum` function verifies the checksum of an uploaded file by comparing the expected checksum with the actual checksum obtained from the S3 object metadata.

After the folder contents are uploaded using `aws s3 sync`, the script iterates over each file in the local directory using `find` and performs checksum verification for each file.

Remember to replace the placeholder values (`your_bucket_name`, `path/to/your/folder/`, `local/directory/to/upload/`, and `your_custom_endpoint_url`) with your actual values.

Save the script to a file, such as `upload_folder_contents.sh`, and make it executable using the command `chmod +x upload_folder_contents.sh`. Then, you can run the script by executing `./upload_folder_contents.sh` in your terminal.