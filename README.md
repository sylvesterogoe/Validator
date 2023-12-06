# Validator
A package for data validation

## Example Usage

```go
func ValidateEmail(v *validator.Validator, email string) {
v.Check(email != "", "email", "must be provided")
v.Check(validator.Matches(email, validator.EmailRX), "email", "must be a valid email address")
}

v := validator.New()
if ValidateEmail(v, email); !v.Valid() {
    // Perform action for a failed validation
return
}
