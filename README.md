
Edit `ForeignKey`, `ManyToManyField` and `CharField` in Django Admin using jQuery UI AutoComplete.

<img src='https://raw.githubusercontent.com/crucialfelix/django-ajax-selects/develop/docs/source/_static/kiss.png
'/>

<img src='https://raw.githubusercontent.com/crucialfelix/django-ajax-selects/develop/docs/source/_static/kiss-all.png
'/>

Documentation
------------------

http://django-ajax-selects.readthedocs.org/en/latest/



Quick Usage
-----------

Define a lookup channel:

```python
# yourapp/lookups.py
from ajax_select import register, LookupChannel
from .models import Tag

@register('tags')
class TagsLookup(LookupChannel):

    model = Tag

    def get_query(self, q, request):
        return self.model.objects.filter(name__icontains=q).order_by('name')[:50]

    def format_item_display(self, item):
        return u"<span class='tag'>%s</span>" % item.name
```

Add field to a form:

```python
# yourapp/forms.py
class DocumentForm(ModelForm):

    class Meta:
        model = Document

    tags = AutoCompleteSelectMultipleField('tags')
```



Fully customizable
------------------

- search query
- query other resources besides Django ORM
- format results with HTML
- custom styling
- customize security policy
- customize UI
- integrate with other UI elements on page using the javascript API
- works in Admin as well as in normal views


Assets included by default
-------------------

- ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js
- code.jquery.com/ui/1.10.3/jquery-ui.js
- code.jquery.com/ui/1.10.3/themes/smoothness/jquery-ui.css

Compatibility
-------------

- Django >=1.5, <=1.9
- Python >=2.7, <=3.4

Contributors
------------

Many thanks to all contributors and pull requesters !

https://github.com/crucialfelix/django-ajax-selects/graphs/contributors


License
-------

Dual licensed under the MIT and GPL licenses:
   http://www.opensource.org/licenses/mit-license.php
   http://www.gnu.org/licenses/gpl.html
