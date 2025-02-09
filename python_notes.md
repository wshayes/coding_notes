# Python

### Pydantic

https://pydantic-xml.readthedocs.io/en/latest/

pydantic-xml extension

### Microsoft tooling

Microsoft Graph API

- https://towardsdatascience.com/querying-microsoft-graph-api-with-python-269118e8180c
- https://keathmilligan.net/automate-your-work-with-msgraph-and-python

## AWS

### Lambda

- https://levelup.gitconnected.com/using-poetry-with-serverless-framework-to-deploy-python-lambda-functions-8dd424727a03
- https://towardsaws.com/how-to-deploy-python-packages-for-aws-lambda-with-layers-acb70e75a3df

### General Tooling

[Ruff](https://beta.ruff.rs/docs/) - Rust-based Python Linter

[pyproject.toml](https://www.notion.so/pyproject-toml-cc148d3d82d647978f33ca1d0d191636?pvs=21)

## GUIs

- Textual - https://textual.textualize.io/
- Beeware Briefcase - [https://beeware.org](https://beeware.org/)

## Tips

- Merging multiple decorators - https://stackoverflow.com/a/5409569/886938 and https://adamj.eu/tech/2020/04/01/how-to-combine-two-python-decorators/
    
    ```python
    # Example from StackOverflow link
    def composed(*decs):
        def deco(f):
            for dec in reversed(decs):
                f = dec(f)
            return f
        return deco
    
    # Then
    
    @composed(dec1, dec2)
    def some(f):
        pass
    
    # is equivalent to
    
    @dec1
    @dec2
    def some(f):
        pass
    
    ###############################################################
    # Example from Adam Johnson link
    @require(methods=["GET", "POST"], login=False)
    def blog(request):
    
    def require(methods=("GET", "POST"), login=True):
        def decorator(func):
            wrapped = func
            if methods is not None:
                wrapped = require_http_methods(methods)(func)
            if login:
                wrapped = login_required(func)
            return wrapped
    
        return decorator
    ```
    
-