# proxly

[![Python](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-GPL%20v3-blue.svg)](LICENSE)

HTTP proxy library for Python using CroxyProxy infrastructure.

## Installation

```bash
pip install proxly
```

## Usage

```python
import proxly

# Simple usage
response = proxly.get("https://example.com")
print(response.text)

# Session-based
proxy = proxly.proxly()
response = proxy.get("https://example.com/api")
proxy.close()

# Context manager
with proxly.proxly() as proxy:
    response = proxy.get("https://example.com")

# Get available servers
servers = proxly.get_server_list()
print(f"Available servers: {len(servers)}")
```

## API

### proxly Class

```python
proxly(timeout=30, max_retries=3)
```

**Methods:**
- `get(url, **kwargs)`
- `post(url, **kwargs)`  
- `put(url, **kwargs)`
- `delete(url, **kwargs)`
- `head(url, **kwargs)`
- `patch(url, **kwargs)`
- `get_session_info()`
- `close()`

### Convenience Functions

```python
proxly.get(url, **kwargs)
proxly.post(url, **kwargs)
proxly.put(url, **kwargs)
proxly.delete(url, **kwargs)
proxly.head(url, **kwargs)
proxly.patch(url, **kwargs)
```

### Server Management

```python
proxly.get_server_list()     # Get list of available proxy servers
proxly.clear_server_cache()  # Clear cached server list
```

## Error Handling

```python
try:
    response = proxly.get("https://example.com")
except proxly.ProxyError as e:
    print(f"Proxy error: {e}")
```

## Requirements

- Python 3.9+
- curl-cffi

## License

GNU General Public License v3.0
