# SSH Security Auditor

⚠️ **EDUCATIONAL PURPOSE ONLY** - This tool is designed for authorized security testing and educational purposes. Only use on SSH servers you own or have explicit written authorization to test.

## Overview

A lightweight SSH security auditing tool that checks SSH service availability, grabs banners, and optionally tests credentials. Designed for lab environments and authorized security assessments.

## Features

- **Banner Grabbing**: Retrieves SSH service banners
- **Port Checking**: Verifies SSH service availability
- **Credential Testing**: Optional credential testing (lab-only)
- **Safety Controls**: Validates targets before scanning
- **Simple & Fast**: Minimal dependencies, easy to use

## Installation

### Requirements

- Python 3.8+
- Standard library only (no external dependencies!)

### Setup

```bash
# Clone the repository
git clone https://github.com/5h4d0wn1k/ssh-auditor.git
cd ssh-auditor

# No installation needed!
python ssh_audit.py --help
```

## Usage

### Basic Usage

```bash
# Check SSH service and grab banner
python ssh_audit.py --host 192.168.1.100 --port 22
```

### With Credential Testing

```bash
# Test credentials from file
python ssh_audit.py \
  --host 192.168.1.100 \
  --port 22 \
  --creds credentials.txt
```

### Custom Timeout

```bash
# Set custom timeout
python ssh_audit.py \
  --host 192.168.1.100 \
  --port 22 \
  --timeout 5.0
```

## Command-Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `--host` | Target host (required) | - |
| `--port` | SSH port | 22 |
| `--timeout` | Connection timeout (seconds) | 3.0 |
| `--creds` | Credentials file (user:pass format) | - |

## Credentials File Format

The credentials file should contain one credential pair per line in `username:password` format:

```
admin:password123
root:toor
user:pass
test:test123
```

## Output Format

```
⚠️  Authorized use only. Test only SSH services you own/control.
[+] Banner: SSH-2.0-OpenSSH_8.0
[*] admin:password123 -> attempted (no auth performed)
[*] root:toor -> attempted (no auth performed)
```

## Examples

### Example 1: Basic SSH Check

```bash
# Check SSH service on default port
python ssh_audit.py --host 192.168.1.100
```

### Example 2: Custom Port

```bash
# Check SSH on custom port
python ssh_audit.py --host 192.168.1.100 --port 2222
```

### Example 3: Credential Testing

```bash
# Test credentials
python ssh_audit.py \
  --host 192.168.1.100 \
  --port 22 \
  --creds common_creds.txt
```

## Safety Features

- **Target Validation**: Validates host before scanning
- **Authorized Use Only**: Designed for systems you own or have permission to test
- **Rate Limiting**: Built-in delays prevent account lockouts

## Use Cases

- **Security Audits**: Check SSH configuration on your servers
- **Penetration Testing**: Authorized security assessments
- **Educational Purposes**: Learn about SSH security auditing

## Legal Disclaimer

⚠️ **IMPORTANT**: This tool is for authorized security testing and educational purposes only. Unauthorized access attempts are illegal.

- Only test SSH servers you own or have explicit written authorization to test
- Respect account lockout policies
- Follow responsible disclosure practices
- Comply with all applicable laws and regulations

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is for educational purposes only. Use responsibly and ethically.

---

**Remember**: Always get explicit authorization before testing any SSH server!
