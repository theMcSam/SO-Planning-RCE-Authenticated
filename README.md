# SOplanning Remote Code Execution Exploit

This script exploits a remote code execution vulnerability in the SOplanning project management tool by uploading a malicious PHP web shell via the file upload functionality. Once the exploit is successful, it provides an option for an interactive shell for further exploitation.

## Features
- **Login and Session Management**: Automatically logs into SOplanning using provided credentials.
- **PHP Web Shell Upload**: Uploads a PHP shell to the server via file upload.
- **Command Execution**: Allows executing arbitrary shell commands via the uploaded web shell.
- **Interactive Shell**: Provides an interactive command execution interface after successful upload.

## Requirements
- Python 3.x
- `requests` library: Install via `pip install requests`

## Usage

### Syntax

```bash
python3 exploit.py -t <target-url> -u <username> -p <password>
```

### Arguments

- `-t` or `--target`: Target URL, including the port if needed (e.g., `http://example.com:8080`).
- `-u` or `--username`: Username to authenticate to the SOplanning instance.
- `-p` or `--password`: Password for the given username.

### Example

```bash
python3 exploit.py -t http://example.com:9090 -u admin -p admin
```

This will:
1. Log into the target SOplanning instance.
2. Upload the PHP web shell to the server.
3. Output the location of the web shell for further exploitation.

### Interactive Shell

After a successful exploit, you will be prompted to enter an interactive shell. If you choose "yes", you can run commands directly on the remote server from your terminal.

Example prompt after upload:
```bash
[+] Uploaded ===> Success message
[+] Exploit completed.
Access webshell here: http://example.com/upload/files/abcd123/xyz.php?cmd=<command>
Do you want an interactive shell? (yes/no) yes
soplaning:~$ whoami
root
soplaning:~$
```

### Manually Accessing the Web Shell

If you prefer not to use the interactive shell, you can directly access the web shell in your browser or via `curl` at the given URL:
```bash
http://<target-url>/upload/files/<link-id>/<php-filename>.php?cmd=<your-command>
```

### Example of Manual Usage:

```bash
curl "http://example.com/upload/files/abcd123/xyz.php?cmd=id"
```

## Important Notes

- Use this script only for ethical purposes, such as penetration testing or security research with proper authorization.
- The author is not responsible for any misuse of this script.

## License

This script is provided for educational purposes only. It is licensed under the MIT License.
