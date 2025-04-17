# Description
**libEconomy** is a PocketMine-MP library that helps you handle economy without doing extra coding. I do all that for you.

All you have to do is call the functions you need!

This library supports BedrockEconomy or EconomyAPI!

Make sure you have either [BedrockEconomy](https://poggit.pmmp.io/p/BedrockEconomy/4.0.4) or [EconomyAPI](https://poggit.pmmp.io/ci/ACM-PocketMine-MP/EconomyAPI/EconomyAPI)!

# Add this to your .poggit.yml
```php
- src: Terpz710/libEconomy/libEconomy
  version: ^1.0.0
```

# Install it to your composer.json
```php
composer require terpz710/libeconomy
```

# API
**How to retrieve a players balance:**
```php
/* $player is instanceof Player **/
use pocketmine\player\Player;

/* Import this class **/
use terpz710\libeconomy\libEconomy;

libEconomy::getInstance()->getMoney($player, function(float $balance) use ($player) {
    $player->sendMessage("Your current balance is: " . $balance);
});
```

**How to add money to a players balance**
```php
/* $player is instanceof Player **/
use pocketmine\player\Player;

/* Import this class **/
use terpz710\libeconomy\libEconomy;

$amount = 100;

libEconomy::getInstance()->addMoney($player, $amount, function(bool $success) use ($player, $amount) {
    if ($success) {
        $player->sendMessage("You have received $" . $amount);
    } else {
        $player->sendMessage("Failed to add money to your account...");
    }
});
```

**How to remove money from a players balance**
```php
/* $player is instanceof Player **/
use pocketmine\player\Player;

/* Import this class **/
use terpz710\libeconomy\libEconomy;

$amount = 100;

libEconomy::getInstance()->reduceMoney($player, $amount, function(bool $success) use ($player, $amount) {
    if ($success) {
        $player->sendMessage("$" . $amount . " have been deducted from your balance");
    } else {
        $player->sendMessage("You don't have enough money or an error occurred");
    }
});
```
