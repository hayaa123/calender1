# insallation 

1. pip install ls.joyous
2. pip install holidays==0.12

### important note:
------
*for this project holidays package version 0.13 not combatable with last version of joyous, for this reason you should install version 0.12.*


3. add it into INSTALLED_APPS:
```
  INSTALLED_APPS = [
    ...
    'ls.joyous',
    'wagtail.contrib.modeladmin',
    ...
]
```
4. Make sure USE_TZ is set to True at (settings.py) `USE_TZ = True`
5. in your terminal:
    - python manage.py migrate
    - python manage.py collectstatic --no-input
    - python manage.py runserver

6. in models.py `from ls.joyous.models import (MultidayEventPage, RecurringEventPage, MultidayRecurringEventPage, removeContentPanels)`
7. in models.py of your app you can add this line to remove some un-wanted fields `removeContentPanels(["category", "tz", "group_page", "website"])`
and you can also hide some unnecessary types of events by:
    ```
    MultidayEventPage.is_creatable = False
    RecurringEventPage.is_creatable = False
    MultidayRecurringEventPage.is_creatable = False
    
    ```
9. in setteings.py:
    joyous settings:
    ```
    JOYOUS_THEME_CSS = "/static/joyous/css/joyous_forest_theme.css" --> joyous theme
    JOYOUS_HOLIDAYS = "Scotland" --> your country if holidays package support it to check it go to: https://github.com/dr-prodigy/python-holidays
    JOYOUS_DATE_FORMAT = "l jS \\o\\f F X"
    JOYOUS_DATE_SHORT_FORMAT = "j M X"
    JOYOUS_TIME_FORMAT = "fq" --> for times like '9am'
    JOYOUS_TIME_INPUT = "12" -->  to enter times in the 12 hour format
    ```
    
    django settings:
    ```
    USE_TZ = True 
    TIME_ZONE = "Europe/London" --> time zone for your country
    USE_I18N = True --> turns on the Django translation system.
    USE_L10N = True --> enables Django’s localized formatting of numbers and dates.
    LANGUAGE_CODE = 'en-uk'
    ```

10. go to admin site and add a `Calendar page` as a child page for your home
11. add a title
11. add to your calender page a child page from these:
    - Event page: a single event
    - Multiday event page: multi event in a sequance days
    - Multiday recurring event page
    - Recurring event page
12. add event's details
13. publish it and see your calendar with your events ^^.

-------------------


   **for more information you can go to the documentation**
    [docs](https://joyous.readthedocs.io/en/latest/installation.html)
