==========================
Scrapyrt (Scrapy realtime)
==========================

.. image:: https://github.com/scrapinghub/scrapyrt/workflows/CI/badge.svg
   :target: https://github.com/scrapinghub/scrapyrt/actions

.. image:: https://img.shields.io/pypi/pyversions/scrapyrt.svg
    :target: https://pypi.python.org/pypi/scrapyrt

.. image:: https://img.shields.io/pypi/v/scrapyrt.svg
    :target: https://pypi.python.org/pypi/scrapyrt

.. image:: https://img.shields.io/pypi/l/scrapyrt.svg
    :target: https://pypi.python.org/pypi/scrapyrt

.. image:: https://img.shields.io/pypi/dm/scrapyrt.svg
   :target: https://pypistats.org/packages/scrapyrt
   :alt: Downloads count

.. image:: https://readthedocs.org/projects/scrapyrt/badge/?version=latest
   :target: https://scrapyrt.readthedocs.io/en/latest/api.html

Introduction
============

HTTP server which provides API for scheduling Scrapy spiders and
making requests with spiders.

Features
========
* Allows you to easily add HTTP API to your existing Scrapy project
* All Scrapy project components (e.g. middleware, pipelines, extensions) are supported out of the box. 
* You simply run Scrapyrt in Scrapy project directory and it starts HTTP server allowing you to schedule your spiders and get spider output in JSON format.

Note
====
* Project is not a replacement for `Scrapyd <https://scrapyd.readthedocs.io/en/stable/>`_ or `Scrapy Cloud <https://www.zyte.com/scrapy-cloud/>`_ or other infrastructure to run long running crawls
* Not suitable for long running spiders, good for spiders that will fetch one response from some website and return response

Getting started
===============

To install Scrapyrt::

    pip install scrapyrt

Now you can run Scrapyrt from within Scrapy project by just typing::

    scrapyrt

in Scrapy project directory.

Scrapyrt will look for ``scrapy.cfg`` file to determine your project settings,
and will raise error if it won't find one.  Note that you need to have all
your project requirements installed.

Scrapyrt supports endpoint ``/crawl.json`` that can be requested
with two methods.

To run sample `toscrape-css spider`_ from `Scrapy educational quotesbot project`_
parsing page about famous quotes::

    curl "http://localhost:9080/crawl.json?spider_name=toscrape-css&url=http://quotes.toscrape.com/"


To run same spider only allowing one request and parsing url
with callback ``parse_foo``::

    curl "http://localhost:9080/crawl.json?spider_name=toscrape-css&url=http://quotes.toscrape.com/&callback=parse_foo&max_requests=1"



Documentation
=============

`Documentation is available on readthedocs <http://scrapyrt.readthedocs.org/en/latest/index.html>`_.

Support
=======

Open source support is provided here in Github. Please `create a question
issue`_ (ie. issue with "question" label).

Commercial support is also available by `Scrapinghub`_.

.. _create a question issue: https://github.com/scrapinghub/scrapyrt/issues/new?labels=question
.. _Scrapinghub: http://scrapinghub.com

License
=======
ScrapyRT is offered under `BSD 3-Clause license <https://en.wikipedia.org/wiki/BSD_licenses#3-clause_license_(%22BSD_License_2.0%22,_%22Revised_BSD_License%22,_%22New_BSD_License%22,_or_%22Modified_BSD_License%22)>`_.


Development
===========
Development taking place on `Github <https://github.com/scrapinghub/scrapyrt>`_.
