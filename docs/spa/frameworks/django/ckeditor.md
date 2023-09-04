# CKEditor

## Custom CSS

### static/pages/css/custom_ckeditor.css

```css
.django-ckeditor-widget, .cke_editor_id_content {
    width: 100% !important;
    max-width: 821px !important;
}
```

### Inyectar en pages_menu.html

```html
<link href="{% static 'pages/css/custom_ckeditor.css' %}" rel="stylesheet">
```

### Inyectar en admin.py

```python
from django.contrib import admin
from .models import Page

class PageAdmin(admin.ModelAdmin):
    list_display = ('title', 'order')
    
    # Inyectamos nuestro fichero css
    class Media:
        css = {
            'all': ('pages/css/custom_ckeditor.css',)
        }
        
admin.site.register(Page, PageAdmin)
```