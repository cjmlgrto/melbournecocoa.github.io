# MelbourneCocoaHeads Website

Visit the website at: https://www.melbournecocoaheads.com.

## Month-to-month updates (June 2019)

The github repository at http://github.com/melbournecocoa/website is setup to automatically deploy Heroku on merges to the master branch.

- Each month, edit `posts.yml` with a new post
    - Update the front page ordering.
    - Link to the relevant events from `events.yml` for this month. Use the `slug` value.
- Create a PR [similar to this one][https://github.com/melbournecocoa/website/pull/14] with the changes and ask someone in the community to check the details
- Merge the PR, this will deploy the code

From here someone with access to the heroku instance needs to run the migration:

```bash
heroku run -a melbourne-cocoaheads php artisan cocoa:update
```


## Deploying to Heroku manually

```sh
git push heroku master && heroku run php artisan migrate && heroku run php artisan cocoa:update
```

More simply (no migration)

```sh
git push heroku master && heroku run php artisan cocoa:update
```

Starting from scratch. This will clean out the DB, add everything again.

```sh
git push heroku master && heroku run php artisan migrate:refresh && heroku run php artisan cocoa:update --bootstrap
```

## Running Locally

```sh
cp .env.example .env
php artisan key:generate
touch database/database.sqlite
php artisan migrate
php artisan cocoa:update
php artisan serve
```

## Writing Posts

You can write posts by creating new entries in posts.yml.

## Events

Update events.yml with new events in the same format as what's there and you can add more events.

There is a command `cocoa:events-2017` that populates the events.yml with a base set of 2017 events.
This will replace the existing file.

## API

See http://localhost:8080/api or https://www.melbournecocoaheads.com/api

## Feed

https://github.com/RoumenDamianoff/laravel-feed

## iCal Feed

http://stevethomas.com.au/php/how-to-build-an-ical-calendar-with-php-and-mysql.html

https://github.com/ahmad/ics.generator

Headers (From Existing):

```
Content-Type: text/calendar; charset=UTF-8
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
```

Existing Calendar:

https://calendar.google.com/calendar/ical/rrb183sckdpi5pi4hrk5u36dbc%40group.calendar.google.com/public/basic.ics

```sh
curl -i https://calendar.google.com/calendar/ical/rrb183sckdpi5pi4hrk5u36dbc%40group.calendar.google.com/public/basic.ics
```

## Open Graph

https://github.com/artesaos/seotools

Twitter cards: https://dev.twitter.com/cards/getting-started

Open graph: http://ogp.me

## Graphics

Favicon.ico

## Sitemap

- https://github.com/RoumenDamianoff/laravel-sitemap
- https://github.com/RoumenDamianoff/laravel-sitemap/wiki/Dynamic-sitemap

## JS

 - Imported OwnCarousel.js https://github.com/smashingboxes/OwlCarousel2
