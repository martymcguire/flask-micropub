Flask-Micropub
==============

A Flask extension to support IndieAuth and Micropub clients.

Authentication
--------------

Authentication uses the
`IndieAuth <https://indiewebcamp.com/IndieAuth>`__ flow to confirm a
user controls a particular URL, without requesting any sort of
permissions or access token. Annotate an endpoint with
``@micropub.authenticated_handler`` and then call
``micropub.authenticate`` to initiate the login.

Authorization
-------------

Authorization uses the full
`Micropub <https://indiewebcamp.com/Micropub>`__ flow to authenticate a
user and then request an access token with which to make micropub
requests. Annotate an endpoint with ``@micropub.authorized_handler`` and
then call ``micropub.authorize`` to initiate the login.

CSRF
----

MicropubClient provides a simple mechanism to deter Cross-Site Request
Forgery. Based on `this Flask
snippet <http://flask.pocoo.org/snippets/3/>`__, we generate a random
string, pass it to the indieauth service via the state parameter, and
then confirm we get the same random string back later.

This helps prevent malicious sites from sending users to your indieauth
endpoint against their will.
