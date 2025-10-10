This is a symfony 7 app.

## Completed

- ✅ Add on the "/" path a login page with a form
- ✅ When the user is connected bring them to the /dashboard page where their name and email is printed

## Implementation Details

The login system has been fully implemented with:
- User entity with email, name, and password fields
- Security configuration with form login authentication
- Login page at "/" with CSRF protection
- Dashboard page at "/dashboard" showing user's name and email
- Logout functionality
- Test user: test@fortrabbit.com (password hashed in database)
