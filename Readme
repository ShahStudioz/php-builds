# PHP Builds

Automated cross-platform PHP builds for Linux, macOS, and Windows with pre-compiled binaries and checksums.

## Overview

This repository provides pre-built PHP binaries for multiple platforms and architectures:

- **Linux**: x64 and ARM64 (aarch64)
- **macOS**: ARM64 (Apple Silicon)
- **Windows**: x64

All builds include commonly used extensions and are optimized for production use.

## Supported Versions

Currently available PHP versions:

- PHP 8.1.34
- PHP 8.2.30
- PHP 8.3.29
- PHP 8.4.16
- PHP 8.5.1

## Getting Started

### Download Binaries

Visit the [Releases](https://github.com/ShahStudioz/php-builds/releases) page to download pre-built binaries for your platform.

Each release includes:
- Compiled PHP binary
- PHP-FPM (Linux)
- Common extensions (curl, gd, mbstring, etc.)
- `php.ini` with recommended settings
- SHA256 checksums

### Verify Downloads

All releases provide checksums for security verification:

```bash
sha256sum -c checksums.txt
```

### Extract and Run

**Linux/macOS:**
```bash
tar -xzf php-X.X.X-<platform>.tar.gz
./bin/php --version
```

**Windows:**
```powershell
Expand-Archive -Path php-X.X.X-windows-x64.zip -DestinationPath php
php\bin\php.exe --version
```

## Included Extensions

All builds include the following PHP extensions:

### Core Extensions
- bcmath
- bz2
- calendar
- ctype
- curl
- dom
- exif
- fileinfo
- ftp
- gd
- gettext
- gmp
- intl
- mbstring
- mysqli
- opcache (enabled by default)
- pdo_mysql
- pdo_pgsql
- pdo_sqlite
- pgsql
- phar
- posix
- readline
- session
- shmop
- simplexml
- soap
- sockets
- sodium
- sqlite3
- tokenizer
- xml
- xmlreader
- xmlwriter
- xsl
- zip
- zlib

## Platform-Specific Notes

### Linux
- Built from source on both x64 and ARM64 runners
- FPM (FastCGI Process Manager) included
- Binary location: `opt/php/bin/php`
- Extension directory: `opt/php/lib/php/extensions`

### macOS
- Built using Homebrew (`php@X.Y` formula)
- Native ARM64 (Apple Silicon) support
- Binaries are code-signed and relocated
- Binary location: `runtime/bin/php`
- Extension directory: `runtime/lib/php/extensions`

### Windows
- Non-thread-safe (NTS) build
- VS17 for PHP 8.4+, VS16 for earlier versions
- Binary location: `bin/php.exe`
- Extensions in: `bin/ext/`

## Build System

### Automated Releases

Releases are created using GitHub Actions workflows:

1. **Linux Build** ([`linux.yml`](.github/workflows/linux.yml))
   - Compiles PHP from source with all extensions
   - Builds for both x64 and ARM64 architectures
   - Creates `.tar.gz` packages

2. **macOS Build** ([`mac.yml`](.github/workflows/mac.yml))
   - Uses Homebrew for dependency management
   - Bundles all required dylibs into portable package
   - ARM64 native compilation

3. **Windows Build** ([`build-windows.yml`](.github/workflows/build-windows.yml))
   - Downloads official PHP binaries
   - Configures php.ini with common settings
   - Creates `.zip` package

4. **Release Controller** ([`release-controller.yml`](.github/workflows/release-controller.yml))
   - Orchestrates all build workflows
   - Generates SHA256 checksums
   - Creates GitHub release with artifacts
   - Updates [`manifest.json`](manifest.json) with download links

### Release Manifest

The [`manifest.json`](manifest.json) file contains metadata for all available versions:

```json
{
  "versions": {
    "8.5.1": {
      "release_date": "2026-02-10",
      "platforms": {
        "linux-x64": {
          "url": "https://github.com/ShahStudioz/php-builds/releases/download/php-8.5.1/...",
          "checksum": "SHA256_HASH",
          "bin": "opt/php/bin/php"
        },
        ...
      }
    }
  }
}
```

## Creating a New Release

To release a new PHP version:

1. Go to **Actions** → **Release Controller**
2. Click **Run workflow**
3. Enter PHP version (e.g., `8.5.2`)
4. Optionally mark as pre-release
5. Click **Run workflow**

The action will:
- Build for all platforms
- Generate checksums
- Create a GitHub release
- Update manifest.json automatically

## Configuration

### PHP.ini Settings

All builds include optimized `php.ini` with:

```ini
memory_limit = 512M
max_execution_time = 300
upload_max_filesize = 100M
post_max_size = 100M
display_errors = On
opcache.enable = 1
opcache.memory_consumption = 256
```

Modify these values by editing `php.ini` in the extracted directory.

## System Requirements

- **Linux**: glibc 2.29+ (Ubuntu 20.04+, Debian 10+)
- **macOS**: 11.0+ (Intel and Apple Silicon)
- **Windows**: Windows 10+ (x64)

## License

These builds are based on the official [PHP source code](https://www.php.net/) which is licensed under the PHP License v3.01.

## Support

For issues or feature requests, please open a [GitHub Issue](https://github.com/ShahStudioz/php-builds/issues).

## Contributing

Contributions are welcome! Please feel free to submit pull requests for improvements to the build configurations or documentation.

---

**Repository:** [ShahStudioz/php-builds](https://github.com/ShahStudioz/php-builds)