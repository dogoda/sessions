# sessions
A non-blocking session handler for PHP


Quick Examples
--------------

```php
$session = new \Dogoda\Sessions\SessionInstance("my-app");
$session->set("current-status", 4);
$currentStatus = $session->get("current-status");
$session->exists("current-status"); #true
```

Avoid common key clashes:
```php
$session->set("user", "Mark");

$backend = $session->createNamespace("backend");
$backend->set("user", "Caroline");

$session->get("user"); # "Mark"
$backend->get("user"); # "Caroline"
```

Store one-time flash messages:
```php
$session->setFlash("message", "Your profile has been updated");

$session->getFlash("message"); # "Your profile has been updated";

$session->getFlash("message"); # null;
```

There is also a static class you can use with all the features above:
```php
use \Dogoda\Sessions\Session;
Session::name("my-apps");

Session::set("current-status", 4);
$currentStatus = Session::get("current-status");

$session::set("user", "Mark");
$session::exits("user"); #true
$session::exits("password"); #false
$backend = $session::createNamespace("backend");
$backend::set("user", "Caroline");

$session::get("user"); # "Mark"
$backend::get("user"); # "Caroline"
```

Inspired by duncan3dc/sessions
