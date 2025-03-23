# Django Notes

See for more Django Notes - https://github.com/wshayes/django_templates

### [**Deploying a Django project to AWS using GitHub Actions and CodeDeploy Blue/Green Deployment + EC2**](https://github.com/Andrew-Chen-Wang/cookiecutter-django-ec2-github) (Works w/ Flask/FastAPI/Rails)

### [**Django Model Fields With Attributes**](https://jacobian.org/til/django-model-fields-with-attributes/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_185) - Jacob Kaplan-Moss

### [Django shell colors: dev, staging or production?](https://django.wtf/blog/django-shell-colors-by-development-environment/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_183)

### [Coding Style](https://docs.djangoproject.com/en/4.2/internals/contributing/writing-code/coding-style/)

### [Django Snippets](https://djangosnippets.org/)

### [Datatables](https://www.youtube.com/playlist?list=PLEoCKCuqTqMiwtsXDX4mVfXC1QUU3FDvF)

[Tabulator](https://github.com/olifolkerd/tabulator)

[Django-tables2](https://github.com/jieter/django-tables2)

[Draftail](https://github.com/thibaudcolas/django-draftail)

## Tutorials

- [Django Wednesday - Codemy.com](https://www.youtube.com/playlist?list=PLCC34OHNcOtqW9BJmgQPPzUpJ8hl49AGy)
- [Bugbytes](https://www.bugbytes.io/)
- [Falco](https://falco.oluwatobi.dev/)

## Example projects

- https://github.com/olksndrdevhub/just-notes-htmx - nice project with Auth, HTMX and Tailwind
- Andreas Jud - https://github.com/andyjud/backend-tutorial
- Notifications using SSE (preferred solution is combo of two below - SSE, Postgres, HTMX)
    - https://github.com/luciddan/htmx-notifications - using SSE, Redis and HTMX and [Youtube talk](https://www.youtube.com/watch?v=MziqE_2Euss)
    - https://valberg.dk/django-sse-postgresql-listen-notify.html - using SSE, Postgres Notify/Listen, and NOT HTMX

[Django useful commands](https://www.notion.so/Django-useful-commands-17a54dbbea414cc0a6a5fd0913cf1862?pvs=21)

## Useful modules
- [Django Axes](https://medium.com/django-unleashed/enhancing-django-security-prevent-brute-force-attacks-with-django-axes-6cf50a15711d) - blocks bad login attempts

- 
## Tips and Code Snippets

Using partials for components

```python
{% include "components/button.html" with value="Feedback" url=context.feedback_url %}
```

---

Add form help to Info icon

```html
<img src='/static/img/icons/help.gif' title='{help_text}' />
```

---

- Composing filtered querysets using Q objects - https://stackoverflow.com/questions/34739680/how-to-add-filters-to-a-query-dynamically-in-django
    
    ```python
    # One example from article
    queryset = Book.objects.all()
    if request.POST.get('age'):
        queryset = queryset.filter(author__age=request.POST['age'])
    if request.POST.get('gender'):
        queryset = queryset.filter(author__gender=request.POST['gender'])
    ```
    
- Get object or 404
    
    ```python
    # https://spookylukey.github.io/django-views-the-right-way/detail-view.html
    # imports
    from django.shortcuts import get_object_or_404
    
    # in the view somewhere
    product = get_object_or_404(Product.objects.all(), slug=slug)
    # Can use product = get_object_or_404(Product, slug=slug) instead, but using the QuerySet instead of the Model is more explicit
    ```
    
- Get query param
    
    ```python
    # In View function
    query_param = request.GET.get("key", "default")  # if default is not defined, default is None
    ```
    

- [Pony Express](https://django-pony-express.readthedocs.io/en/latest/index.html) - Classed based email templates
- [Django Prose](https://github.com/withlogicco/django-prose) - Rich text mgmt package
- Watson - search package
- [Psycopg3 installation](https://learndjango.com/tutorials/psycopg3-binary-and-django-42-installation-quick-t)
- Simplifying decorators - [Merging multiple decorators - https://stackoverflow.com/a/5409569/886938 and https://adamj.eu/tech/2020/04/01/how-to-combine-two-python-decorators/](https://www.notion.so/Merging-multiple-decorators-https-stackoverflow-com-a-5409569-886938-and-https-adamj-eu-tech-2-6be8037fb7d7435f97e50f16675469bc?pvs=21)

## Tools

- https://github.com/anze3db/django-tui - Text-based User Interface for Django commands
- 

## Task processing

Tip - use Postgres queue technology instead of Redis, etc

- https://procrastinate.readthedocs.io/en/stable/index.html
- https://levelup.gitconnected.com/asynchronous-processing-of-database-events-in-a-robust-and-lightweight-manner-using-django-pgpubsub-cfb0dcf12803
- 

["Lazy load" of data from a context processor](https://www.notion.so/Lazy-load-of-data-from-a-context-processor-882ff78c17a740afa7a705d456d3e632?pvs=21)

[Django Views — The Right Way](https://www.notion.so/Django-Views-The-Right-Way-ec12c254351749f1ac41ed277aa7ad57?pvs=21)

[](https://rsinger86.github.io/django-lifecycle/)

- Django Lifecycle Hooks
    
    This project provides a `@hook` decorator as well as a base model and mixin to add lifecycle hooks to your Django models. Django's built-in approach to offering lifecycle hooks is [Signals](https://docs.djangoproject.com/en/dev/topics/signals/). However, my team often finds that Signals introduce unnecessary indirection and are at odds with Django's "fat models" approach.
    
    In short, you can write model code like this:
    
    ```
    from django_lifecycle import LifecycleModel, hook, BEFORE_UPDATE, AFTER_UPDATE
    class Article(LifecycleModel):
        contents = models.TextField()
        updated_at = models.DateTimeField(null=True)
        status = models.ChoiceField(choices=['draft', 'published'])
        editor = models.ForeignKey(AuthUser)
        @hook(BEFORE_UPDATE, when='contents', has_changed=True)
        def on_content_change(self):
            self.updated_at = timezone.now()
        @hook(AFTER_UPDATE, when="status", was="draft", is_now="published")
        def on_publish(self):
            send_email(self.editor.email, "An article has published!")
    
    ```
    
    Instead of overriding `save` and `__init__` in a clunky way that hurts readability:
    
    ```
        # same class and field declarations as above ...
        def __init__(self, *args, **kwargs):
            super().__init__(*args, **kwargs)
            self._orig_contents = self.contents
            self._orig_status = self.status
        def save(self, *args, **kwargs):
            if self.pk is not None and self.contents != self._orig_contents):
                self.updated_at = timezone.now()
            super().save(*args, **kwargs)
            if self.status != self._orig_status:
                send_email(self.editor.email, "An article has published!")
    
    ```
    
    ## Requirements
    
    - Python (3.5+)
    - Django (2.0+)
    
    ## Installation
    
    ```
    pip install django-lifecycle
    
    ```
    
    ## Getting Started
    
    Either extend the provided abstract base model class:
    
    ```
    from django_lifecycle import LifecycleModel, hook
    class YourModel(LifecycleModel):
        name = models.CharField(max_length=50)
    
    ```
    
    Or add the mixin to your Django model definition:
    
    ```
    from django.db import models
    from django_lifecycle import LifecycleModelMixin, hook
    class YourModel(LifecycleModelMixin, models.Model):
        name = models.CharField(max_length=50)
    
    ```
    
    ## (Optional) Add `django_lifecycle` to your `INSTALLED_APPS`
    
    ```
    INSTALLED_APPS = [
        # ...
        "django_lifecycle_checks",
        # ...
    ]
    
    ```
    
    This will raise an exception if you forget to add the mixin or extend the base model class.
    
    [Read on](https://rsinger86.github.io/django-lifecycle/examples/) to see more examples of how to use lifecycle hooks.
