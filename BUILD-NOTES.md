# Build Notes for Debian Trixie

## Dependencies

The molior build system has been updated to handle missing custom dependencies gracefully:

### Available in Standard Debian Repositories
- debhelper-compat (= 13)
- python3-all (>= 3.13) 
- python3-setuptools
- python3-pytest, python3-pytest-cov, python3-coverage
- python3-mock, python3-yaml, python3-sqlalchemy
- python3-jinja2, python3-tz, flake8, git

### Custom Dependencies (May Not Be Available)
- python3-cirrina (>= 0.4.7)
- python3-launchy
- python3-async-cron
- python3-giturlparse
- python3-aiofile

## Build Process

When building with `debuild -us -uc`, the system will:

1. Check for availability of custom dependencies
2. Skip tests that require unavailable packages
3. Continue with the build process
4. Produce packages with runtime dependencies intact

This allows molior to be built on standard Debian Trixie systems while maintaining full functionality when all dependencies are available.

## Development

For development environments where custom dependencies are available, install them using:

```bash
pip3 install -r requirements-build.txt
```