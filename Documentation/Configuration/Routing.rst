Routing
^^^^^^^

Since TYPO3 there is a modern routing mechanims. Please use this to create real/speaking urls.

It is also possible to handle e.g. the XML sitemp. This is the example configuration for a /sitemap.xml incl. sub sitemaps without cHash to get this sitemaps to the StaticFileCache:

.. code-block:: nginx

   routeEnhancers:
      PageTypeSuffix:
         type: PageType
         default: ''
         map:
            'sitemap.xml': 1533906435
      SitemapNames:
         type: Simple
         routePath: '/s/{sitemap}'
         requirements:
            sitemap: '.*'
         _arguments:
            sitemap: 'sitemap'
         aspects:
            sitemap:
               type: StaticValueMapper
               map:
                  pages: 'pages'
                  ext_news: 'ext_news'
