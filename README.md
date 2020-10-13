# PHP File Watcher with Socket.IO

Watch your PHP files and others, send event notification to browser, then get notifify with Socket.IO JS.
And also, you can make browser auto-reload or auto-refresh when file has changed.

## Usage

Download [Socket.IO JS](https://socket.io), then put the following script:

```js
var socket = io('http://127.0.0.1:2021');
socket.on('file_update', function (data) {
  console.log(data);
  window.location.reload();
});
```

Download PHAR (``watch``) file from this repo, the file size only _**160kB**_.

Open your terminal from your root project directory. Start with the following commands:

```bash
$ php watch start
```

with daemon, you can run background process without terminal window:

```bash
$ php watch start -d
```

See information about all options:

```bash
$ php watch
```

For more information please visit [walkor/workerman](https://github.com/walkor/Workerman)'s repo.

## Additional Config/Options

You can not set specific directory from your terminal, but you can do this with more options:

This config is hitchhiking within ``composer.json`` file:

```json
{
    "enixapp": {
        "watcher": {
            "port": 2021,
            "directory": "./",
            "extensions": ["php", "js", "css", "html", "md"],
            "cache-dir": "./writable/cache/"
        }
    }
}
```

These are two files ``watcher.log`` and ``watcher.pid`` which automatically created in your root directory project if the ``cache-dir`` doesn't exists.

## Built with

1. Box (https://github.com/box-project/box).
2. Workerman (https://github.com/walkor/Workerman).

