# feeds.cocoapods.org - RSS and Twitter updates for new pods

This application creates and updates an RSS feed containing the
last 30 pods added to [CocoaPods/specs](https://github.com/CocoaPods/specs).
During each update it tweets the new pods.

## Application

- Running on Ruby 1.9.2/3.
- Procfile-based Sinatra application.
- Requires a host caplable of managing a git repository.
- Available at http://feeds.cocoapods.org [Not working yet].
- Based on [cococapods.org](https://github.com/CocoaPods/CocoaPods.org).

## Setup

```shell
$ cp .env.sample .env
$ vim .env
$ bundle install
$ foreman start
```

Test GitHub [post-receive hook](http://help.github.com/post-receive-hooks/):

```shell
$ curl -d 'payload={"ref":"refs/heads/master"}' http://localhost:5000/hook
```

## Events

- Initialization:
    1. the specs repo is cloned or updated in `tmp/.cocoapods/master`.
    2. the feed is created in `public/new-pods.rss`.
- GitHub post-receive hook:
    1. the specs repo is updated.
    2. the feed is recreated.
    3. tweets for the new pods.

## License

This application and CocoaPods are available under the [MIT license](http://www.opensource.org/licenses/mit-license.php).
