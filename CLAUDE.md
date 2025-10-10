# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Symfony 7.3 application template designed for deployment on fortrabbit. It uses PHP 8.2+ and follows standard Symfony conventions with the MicroKernelTrait architecture.

## Development Commands

### Essential Commands
- **Install dependencies**: `composer install`
- **Run console commands**: `bin/console <command>`
- **Clear cache**: `bin/console cache:clear`
- **List all commands**: `bin/console list`

### Development Server
- **Run dev server**: `symfony serve` (requires Symfony CLI)
- **Run with PHP**: `php -S localhost:8000 -t public`

### Future Development (as per PLAN.md)
The project is planned to include:
- Twig templating engine
- Doctrine ORM for MySQL
- User authentication system
- Login/dashboard functionality

Once these are added, relevant commands will be:
- **Database migrations**: `bin/console doctrine:migrations:migrate`
- **Create migration**: `bin/console make:migration`
- **Database schema update**: `bin/console doctrine:schema:update`

## Architecture

### Core Structure
- **Kernel**: `src/Kernel.php` - Uses `MicroKernelTrait` for simplified configuration
- **Entry point**: `public/index.php` - Symfony Runtime-based bootstrap
- **Console**: `bin/console` - CLI application entry point
- **Configuration**: `config/` directory
  - `bundles.php` - Bundle registration
  - `services.yaml` - Service container configuration
  - `packages/` - Bundle-specific configurations
  - `routes.yaml` - Routing configuration

### Service Configuration
Services in `src/` are auto-wired and auto-configured by default. The service container automatically:
- Injects dependencies based on type-hints
- Registers command classes, event subscribers, etc.
- Creates services with FQCN as service ID

### Environment Configuration
- Uses standard Symfony .env file hierarchy (.env, .env.local, .env.$APP_ENV, etc.)
- `APP_ENV` determines the runtime environment (dev, prod, test)
- `APP_SECRET` must be configured for production (currently empty in .env)
- Environment-specific config in `config/packages/<env>/` directories

### Autoloading
- `App\` namespace maps to `src/` directory (PSR-4)
- `App\Tests\` namespace maps to `tests/` directory (PSR-4)

## Key Conventions

### Controllers
Controllers should extend `Symfony\Bundle\FrameworkBundle\Controller\AbstractController` and use route attributes or YAML configuration.

### Dependency Injection
Prefer constructor injection with type-hinted dependencies. The autowiring system will handle resolution automatically.

### Configuration Management
- Use YAML for service and route configuration
- Environment-specific overrides go in `config/packages/<env>/`
- Use the `when@<env>:` syntax in YAML for environment-specific configuration blocks

## Important Notes

- This is a minimal Symfony skeleton - most bundles need to be added as needed
- Currently only FrameworkBundle is registered
- Cache and logs are stored in `var/` (excluded from git)
- Public assets go in `public/` directory
- The project uses Symfony Flex for recipe management
