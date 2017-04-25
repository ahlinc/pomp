pomp changelog
==============

Here you can see the full list of changes between pomp releases.

Version 0.3.0
-------------

Does not released yet

- `BaseDownloadWorker.get_one(self, request)` -> `BaseDownloadWorker.process(self, request)`
- `BaseDownloader.get(self, requests)` -> `BaseDownloader.process(self, crawler, request)`
- non `BaseRequest` instances are items
- `BaseHttpResponse.get_request()` instead of `BaseHttpResponse.request`
  property
- BaseMiddleware.process_(request|response|exception) now may be awaitable
- BaseCralwer.(process|next_requests|on_processing_done) now may be awaitable
- BaseDownloader.(start|stop) now may be awaitable
- `BaseDownloader.prepare(self)` renamed to `BaseDownloader.start(self,crawler)`
- BasePipeline.(start|stop|process) now may be awaitable
- process `Future` objects without wrapping it with `Planned` object
- asynciotools with async/await syntax
- removed `RUNNING`, `CANCELLED_AND_NOTIFIED`, `exception` method from
  `Planned` class


Version 0.2.1
-------------

Released at 2016-09-12

- fix pipe start/stop/process exception processing
- fix: `AioPomp` ensure_future for process_requests in main loop
- `BaseCrawler.on_processing_done` when request, middlewares, response,
  extract, pipelines processing was done
- count param for `BaseQueue.get_requests` - number allowed concurrent
  requests for current downloader, may be None

Version 0.2.0
-------------

Released at 2016-03-01

- middlewares logic moved to engine and
  BaseMiddleware.process_(request|response|exception) with
  crawler and downloader params
- Downloader does not have any more middlewares param
- BaseDownloaderMiddleware renamed to BaseMiddleware
- BaseDownloderException renamed to BaseCrawlException
- AioConcurrentCrawler with asyncio and concurrent futures support
- pomp.core.item moved to pomp.contrib.item without backward
  compatibility https://github.com/estin/pomp/issues/6#issuecomment-172342598
- AioPomp with asyncio support
- queue semaphore to prevent fetching more requests than downloader can
  process now
- bfo and dfo orders now configured via Pomp constructor
- no recursion, internal queue is used
- twsited is not a part of pomp
- defer object replaced to Planned object (like Future object)


Version 0.1.3
-------------

Will not be released

- crawler `extract_items` method can yield next requests
- process exception on `extract_items` and `next_requests` by downloader
  middlewares
- store result of calling `sys.exc_info` in exception instance

Version 0.1.2
-------------

Released at 2015-05-08

- twistedtools on request timeout can raise ResponseNeverReceived or
  others (see _newcleint twisted api)...
- utils.DeferredList works with deferred and not-deferred objects
- fixed Item object behavior (get item field value)


Version 0.1.1
-------------

Released on December 12nd 2013

- urllib and twisted downloader on get method yield result
- bugfix `depth first` method
- concurrenttools change try/finally to generator behavior
- processing requests through queue
- better generator usage


Version 0.1.0
-------------

Released on June 14nd 2013

- rename SimpleDownloader to UrllibDownloader
- urllib code now in contrib/urllibtools.py
- ENTRY_URL renamed to ENTRY_REQUESTS
- next_url renamed to next_requests
- async support
- Twisted support
- concurrent future support
- pipelines accept crawler on start/stop/process calls
- downloader middleware also process exception


Version 0.0.2
-------------

First public preview release.
