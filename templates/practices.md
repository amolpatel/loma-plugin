# Development Practices

> Patterns, conventions, and rules for maintaining code quality.

---

## Code Style

### General Principles

- **Consistency**: Follow existing patterns in the codebase
- **Simplicity**: Prefer simple solutions over clever ones
- **Readability**: Code is read more often than written

### Naming Conventions

```python
# Variables and functions: snake_case
user_name = "example"
def calculate_total():
    pass

# Classes: PascalCase
class UserAccount:
    pass

# Constants: SCREAMING_SNAKE_CASE
MAX_RETRY_COUNT = 3
```

---

## Testing Conventions

### Unit Tests

- **Location**: `tests/unit/` mirroring source structure
- **Naming**: `test_<module>_<functionality>.py`
- **Coverage**: Aim for critical paths, not 100%

### Test Structure

```python
def test_function_does_expected_behavior():
    # Arrange
    input_data = create_test_data()

    # Act
    result = function_under_test(input_data)

    # Assert
    assert result == expected_value
```

---

## Error Handling

### Exception Hierarchy

```python
# Base exception for the module
class ModuleError(Exception):
    pass

# Specific exceptions
class ValidationError(ModuleError):
    pass

class ConfigurationError(ModuleError):
    pass
```

### Error Response Strategy

- **Validation errors**: Return clear error message to caller
- **External service errors**: Retry with backoff, then fail gracefully
- **Unexpected errors**: Log, alert, fail fast

---

## Logging Standards

### Log Levels

- **ERROR**: System errors requiring immediate attention
- **WARNING**: Unexpected but handled situations
- **INFO**: Normal operations (startup, key events)
- **DEBUG**: Detailed traces (development only)

---

## Configuration Management

### Environment Variables

- **Required**: Fail fast if missing
- **Optional**: Document defaults clearly
- **Secrets**: Never commit, use environment or secret manager

---

## Documentation Standards

### Code Comments

- **Why, not what**: Explain rationale, not obvious code
- **Keep current**: Update comments when code changes

### Loma Updates

- **When**: After user confirms work ("looks good", "ship it")
- **What**: Current system state (not changelog style)
- **Where**: Corresponding domain folder in `loma/`

---

## Related Files

- [Summary](summary.md) - Project overview
- [Terminology](terminology.md) - Domain language
- [Loma Map](loma-map.md) - Documentation index
