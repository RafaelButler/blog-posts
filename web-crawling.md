## Web Scraping with PHP - Spatie Crawler Toolkit for Laravel

Web scraping is a way of collecting data from the internet, and it serves many purposes. It is also called web crawling or data collection.

When we think of something like this, programming languages ​​like Python immediately come to mind, with their incredible libraries to make work easier.

But this is also possible with PHP. We know that this programming language, widely used for building web pages or systems, allows us to collect data.

Before you go out there and try to collect data from websites, you need to know the terms for exploring this data, so you know if you can actually use it without any problems.

## Start Project

There are some PHP packages that we can use to achieve our goal, the focus is to talk about a very interesting package called [Spatie Crawler.](https://github.com/spekulatius/spatie-crawler-toolkit-for-laravel)

We can install using composer:

```php
composer install spatie/crawler
```

In order to use it we need to instantiate the `CrawlerObserver` class:

```php
\Spatie\Crawler\CrawlObservers\CrawlObserver

abstract class CrawlObserver {}
```

There are some very interesting functions in this class:

```php
public function willCrawl(UriInterface $url, ?string $linkText): void {}
```

> This function is called when scraping a URL.

```php
abstract public function crawled(
  UriInterface $url,
  ResponseInterface $response,
  ?UriInterface $foundOnUrl = null,
  ?string $linkText,
): void;
```

> This is the function called after scraping has been performed.

If there is any failure, the `crawlFailed` function is called:

```php
abstract public function crawlFailed(
	UriInterface $url,
	RequestException $requestException,
	?UriInterface $foundOnUrl = null,
	?string $linkText = null,
): void;
```

And finally:

```php
 public function finishedCrawling(): void {}
```

> It is called when scraping is finished

There is a universe of possibilities to be done with this package:

- Multiple Observers
- Request Limit
- Usage with Queues
- Link Extraction
- Parallel Requests

And many other resources that are in its documentation and from where I took all the references.

## References:

- [Spatie Crawler](https://github.com/spekulatius/spatie-crawler-toolkit-for-laravel)
- [Spatie Docs](https://spatie.be/docs)
