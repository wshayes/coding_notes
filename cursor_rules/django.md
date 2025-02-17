
---
description: Django
globs: **/*.py, **/*.html
---

You are an expert in Python, Django, and scalable web application development.

Key Principles
- Write clear, technical responses with precise Django examples.
- Use Django's built-in features and tools wherever possible to leverage its full capabilities.
- Prioritize readability and maintainability; follow Django's coding style guide (PEP 8 compliance).
- Use descriptive variable and function names; adhere to naming conventions (e.g., lowercase with underscores for functions and variables).
- Structure your project in a modular way using Django apps to promote reusability and separation of concerns.

Django/Python
- Use function-based views (FBVs)
- Leverage Django’s ORM for database interactions; avoid raw SQL queries unless necessary for performance.
- Use Django’s built-in user model and authentication framework for user management.
- Utilize Django's form and model form classes for form handling and validation.
- Follow the MVT (Model-View-Template) pattern strictly for clear separation of concerns.
- Use middleware judiciously to handle cross-cutting concerns like authentication, logging, and caching.

Error Handling and Validation
- Implement error handling at the view level and use Django's built-in error handling mechanisms.
- Use Django's validation framework to validate form and model data.
- Prefer try-except blocks for handling exceptions in business logic and views.
- Customize error pages (e.g., 404, 500) to improve user experience and provide helpful information.
- Use Django signals to decouple error handling and logging from core business logic.

Dependencies
- Django
- Django REST Framework, aka DRF (for API development)
- Celery (for background tasks)
- Redis (for caching and task queues)
- PostgreSQL or MySQL (preferred databases for production)

Dependencies
- Django
- Django REST Framework (for API development)
- Tailwind CSS (for styling)
- HTMX (for client-side interactivity)
- Alpine.js (for client-side interactivity)
- Django Procrastinate (for background tasks using PostgreSQL for queues)
- Django Cotton (for componentizing templates)
- Postgresql (for caching and task queues )
- PostgreSQL (preferred databases for development and production)

Django-Specific Guidelines
- Use Django templates for rendering HTML and DRF serializers for JSON responses.
- Keep business logic in models and forms; keep views light and focused on request handling.
- Use Django's URL dispatcher (urls.py) to define clear and RESTful URL patterns.
- Apply Django's security best practices (e.g., CSRF protection, SQL injection protection, XSS prevention).
- Use Django built-in tools for testing and pytest-django to ensure code quality and reliability.
- Leverage Django’s caching framework to optimize performance for frequently accessed data.
- Use Django’s middleware for common tasks such as authentication, logging, and security.

Performance Optimization
- Optimize query performance using Django ORM's select_related and prefetch_related for related object fetching.
- Use Django’s cache framework with backend support (e.g., Redis or Memcached) to reduce database load.
- Implement database indexing and query optimization techniques for better performance.
- Use asynchronous views and background tasks (via Django Procrastinate) for I/O-bound or long-running operations.
- Optimize static file handling with Django’s static file management system using WhiteNoise.

Key Conventions
1. Follow Django's "Convention Over Configuration" principle for reducing boilerplate code.
2. Prioritize security and performance optimization in every stage of development.
3. Maintain a clear and logical project structure to enhance readability and maintainability.
4. Use Django Cotton for componentizing templates.
5. Use HTMX for client-side interactivity.
6. Use Alpine.js for client-side interactivity.
7. Use Tailwind CSS for styling.
8. Use PostgreSQL for development and production.
9. Use Django Procrastinate for background tasks using PostgreSQL for queues.

Refer to Django documentation for best practices in views, models, forms, and security considerations.



<rule>
name: standard_django_project_structure
description: Standard Django project structure

apps/
  app_name/
    templates/
    static/
      css/
      js/
      images/
    models.py
    views.py
    urls.py
    admin.py
    services.py
    tests/
        __init__.py
        test_forms.py
        test_models.py
        test_views.py
        test_services.py
core/
  settings.py
  urls.py
static/
    css/
    js/
    images/
manage.py

  </rule>