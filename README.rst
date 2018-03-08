========================================
Woopra Python client with Django support
========================================

A Pythonic Woopra client with Django support.

Installation
============

::

    pip install woopra-py

Usage
=====

Client configuration
--------------------

At a base level, you can set up the client using keywords or a configuration
dictionary::

>>> import woopra_tracker
>>> config = {'domain': 'www.example.com'}
>>> woopra = woopra_tracker.client(**config)

User identification
-------------------

If you have the user information when you create the tracker instance, you can
add it then::

>>> config = {'domain': 'www.example.com'}
>>> woopra = woopra_tracker.client(user={'email': "bug@insects.com"}, **config)

To add identifying information::

>>> woopra.user['name'] = "Stick Bug"

To identify the user to Woopra::

>>> woopra.push()

Event tracking
--------------

Track a page view::

>>> woopra.track()

Track an event::

>>> woopra.track('purchase')

Add information to the event::

>>> woopra.track('purchase', item='Terrarium', price='50.00')

Django integration
------------------

The Django client construction is a shortcut to use a an HttpRequest instance
to create the tracker.

>>> woopra = woopra_tracker.django(request)

You can pass in missing or alternative values using the keyword pattern here too::

>>> woopra = woopra_tracker.django(request, **config)

However you should be careful doing that as config values added here will *override*
values from the request.

License
=======

MIT license


