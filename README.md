# Bootstrap Builder

This is just a small lil package to make building HTML with Python _hopefully_ a lil easier.

```python
>>> import bootstrap_builder as bb
>>> page = bb.HTMLPage(title="Bootstrap Builder")  # Make a page containing the head and body and etc
>>>
>>> # Time for navbar
>>> navbar_container = page.new_navbar()
>>> print(navbar_container)  # <nav class="navbar" />
>>> navbar_container['class'].append('navbar-expand-sm')  # Add 'navbar-expand-sm' to the class list
>>> print(navbar_container)  # <nav class="navbar navbar-expand-sm" />
>>> with navbar_container.new_navbar_nav() as navbar:
	_ = navbar.new_navbar_nav_item().new_child('a', 'Index', attrs={'href': '/index', 'class': 'nav-link'})  # You can add attrs inside new_XXX methods if you don't want to do it via __setitem__

>>> print(navbar_container)  # <nav class="navbar navbar-expand-sm" ><ul class="navbar-nav"><li class="nav-item"><a href="/index" class="nav-link">Index</a></li></ul></nav>
>>>
>>> child = page.new_child('div')
>>> child['data-test'] = 'test1'  # Add a new attr
>>> child['class'].append('owo')  # Add a new class
>>> print(child)  # <div data-test="test1" class="owo" />
>>>
>>> # Add some content to the tag
>>> child = page.new_child('div')
>>> _ = child.new_child('p', 'Nested Tag')  # This is a nested tag
>>> print(child)  # <div><p>Nested Tag</p></div>
>>>
>>> # We can also just add plain content
>>> child = page.new_child('div')
>>> _ = child.add_child('p', 'New Child')  # Like .new_child, but doesn't create a new object, just adds it to the object
>>> print(child)  # <div>New Child</div>
>>>
```
