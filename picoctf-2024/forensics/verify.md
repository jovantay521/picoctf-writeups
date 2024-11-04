# Verify

**Category:** Forensics  
**Difficulty:** Easy  
**Date:** 2024-11-03

## Challenge Description

```
People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.
```

## Files Provided
- `checksum.txt`: Contains the checksum of the correct file. 
- `decrypt.sh`: Script used to decrypt the file once the hash is verified. 
- `files`: Directory containing multiple files, with the correct file hidden among them.

## Approach & Solution

### Tools Used:
- Bash
- `sha256sum`

### Script:  
```bash
#!/bin/bash

CHALLENGE_DIRECTORY="./home/ctf-player/drop-in"
TARGET_HASH=$(cat "$CHALLENGE_DIRECTORY/checksum.txt")
match_found=false  # Initialize match_found as false

for file in "$CHALLENGE_DIRECTORY/files"/*; do
    file_hash=$(sha256sum "$file" | awk '{print $1}')

    if [[ "$file_hash" == "$TARGET_HASH" ]]; then
        echo "Match found: $file. Decrypting..."
        file_name=$(basename "$file")  # Corrected variable assignment
        sh "$CHALLENGE_DIRECTORY/decrypt.sh" "files/$file_name"
        match_found=true  # Set match_found to true if a match is found
    fi
done

# Check if no matches were found
if ! $match_found; then
    echo "No file matches the checksum."
fi
```

### Explanation:
The script iterates through the `files` directory, comparing the checksum of each file to the given target hash. If a file with a matching checksum is found, the `decrypt.sh` script is executed on it.

## Flag
```
picoCTF{trust_but_verify_e018b574}
```

## Key Takeaways
### Techniques Learned:
- How to use `sha256sum` to compute and verify SHA-256 hashes of files.
- How to use Bash scripting to automate the process of generating and comparing file hashes against a target hash.