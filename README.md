# swagger_ui_dark
Dark Theme for Swagger UI used in Fastapi applications ([swagger-ui-dist](https://cdn.jsdelivr.net/npm/swagger-ui-dist@4/swagger-ui.css)) base on 
[NightEye](https://nighteye.app/dark-css-generator/)

## Usage
You can pass the cdn link to `swagger_css_url` parameter in `get_swagger_ui_html` function in Fastapi

> There are 2 css files,
> - [main-page-dark-css.css](main-page-dark-css.css) - Main css file
> - [main-page-dark-css-min.css](main-page-dark-css-min.css) - Minified version of the 1st one

- **With CDN (statically)**
    - CDN url:
        ```
        https://cdn.statically.io/gh/Retloldin/swagger_ui_dark/main/main-page-dark-css.css
        ```
    - Example:
        ```python
        from fastapi.openapi.docs import get_swagger_ui_html # Needed to edit Swagger UI
        
        app = FastAPI(docs_url=None) # Disable default Swagger UI
        
        @app.get("/docs", include_in_schema=False)
          async def custom_swagger_ui_html_github():
            return get_swagger_ui_html(
            openapi_url=app.openapi_url,
            title=f"{app.title} - Swagger UI",
            swagger_css_url="https://cdn.statically.io/gh/Retloldin/swagger_ui_dark/main/main-page-dark-css.css",
            swagger_ui_parameters={"syntaxHighlight.theme": "monokai"}
        )
        ```
