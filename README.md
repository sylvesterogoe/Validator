# Validator
A package for data validation

## Example Setup
### Create functions with custom validation rules

```go
func ValidateEmail(v *validator.Validator, email string) {
v.Check(email != "", "email", "must be provided")
v.Check(validator.Matches(email, validator.EmailRX), "email", "must be a valid email address")
}

func ValidatePassword(v *validator.Validator, password string) {
	v.Check(password != "", "password", "must be provided")
	v.Check(len(password) >= 8, "password", "must be at least 8 characters long")
	v.Check(len(password) <= 72, "password", "must not be more than 72 characters long")
}
```

## Example Usage
```go
v := validator.New()
if ValidateEmail(v, email); !v.Valid() {
    // Perform action for a failed validation
    return
}

if ValidatePassword(v, password); !v.Valid() {
    // Perform action for a failed validation
    return
}
