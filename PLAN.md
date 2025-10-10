This is a symfony 7 app.

Plan to implement things:

- Add twig templating
- Add orm
- Add a user entity with email, name and password
- Add a migration (for mysql) with the user "test@fortrabbit.com", "Test User" and "password" (hashed with bcrypt)
- Add on the "/" path a login page with a form
- When the user is connected bring them to the /dashboard page where their name and email is printed
