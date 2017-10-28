**************************************************
Common and Useful URL Regular Expression Patterns(regex)
**************************************************
Many time I found myself refering to books to see urlpatterns in django. So I thought to create a quick overview of django urlpatten for use in my projects. 

A typical url instance of django.

.. code-block:: Python

    url(regex, view, kwargs=None, name=None)

This guide is for regex parameter of url.

A typical django url pattern:

.. code-block:: Python

    url(r'^questions/(?P<any_keyword_argument>\d+)/$', views.question_details, name='question_details'),

Above url may seems to be a rumble of punctuation marks. However, it is jus a regular Python.

Notes:

#. **^questions** is telling django to match anything that starts with the word **questions**.
#. / tells djnango that another / should follow.
#. **(?P<any_keyword_argument>\d+)** is a interesting one. It is capturing    value based on regex and assign it to **any_keyword_argument**. Here \\d+ is a regex. \\d matches for single digit from 0 to 9 while **+** says previous item should be repeated at least once.
#. /$ means end of url i.e no another / will appear.


If I have url `http://www.mysite.com/questions/22/ <http://http://www.mysite.com/questins/22>`_  then any_keyword_argument will get the value of 22.

So, to capture any value in keyword argument we must use **(?P<any_keyword_argument> regex)** in our url.

I often use mnemonic for this **Pirate Queen Produces Anaconda** where

* P of Pirate stands for Parenthesis (
* Q of Queen for Question Mark i.e ?.
* P of Produces for letter P.
* A of Anaconda for Angle Brackets i.e <

====
    
******************************************
Common Regular Expressions For Django URls
******************************************

Slugs
=====
**Regex**: (?P<slug>[-\w]+) or (?P<slug>[\w-]+)

.. code-block:: Python

    url(r'^posts/(?P<slug>[-\w]+)/$', views.post, name = 'post'),
    url(r'^posts/(?P<slug>[\w-]+)/$', views.post, name = 'post',

Note: \\w matches a word

Slug::
    
    this-is-a-title-of-beautiful-blog


Primary Key, ID
===========
**Regex**: (?P<pk>\d+)

.. code-block:: Python

    url(r'^questions/(?P<pk>\d+)/$', views.question_details, name='question_details'),

Primary Key::

    pk = 1, pk = 2, 
    e.g questions/22/


Primary Key With Slug
=====================
**Regex**: (?P<slug>[-\w]+)-(?P<pk>\d+)

.. code-block:: Python

    url(r'^post/(?P<slug>[-\w]+)-(?P<pk>\d+)/$', views.post, name = 'post'),

Username
========
**Regex**: (?P<username>[\w.@+-]+)

.. code-block:: Python

    url(r'^profile/(?P<username>[\w.@+-]+)/$', views.user_profile),

Username::
    
    username = AnyRandomUserName or
    username = any@random.com