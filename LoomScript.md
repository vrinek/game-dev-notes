# Graphics

## Loading and displaying a 2D sprite

```
var sprite = CCSprite.createFromFile("assets/logo.png");
sprite.x = 240;
sprite.y = 120;
layer.addChild(sprite);
```

## Displaying a label (text)

```
var label = new Label("assets/Curse-hd.fnt");
label.text = "Hello Tween!";
label.x = 240;
label.y = 240;
layer.addChild(label);
```

## Animating properties of a sprite

> **Tween.to** (target:Object, duration:Number, params:Dictionary \<String Object\>)

```
// Moving fast to a new position
Tween.to(sprite, 0.3, {"x": x, "y": y});

// Getting bigger
Tween.to(sprite, 1, {"scale": 1.5, "ease":EaseType.EASE_OUT_ELASTIC});

// Combining animations
Tween.to(sprite, 0.3, {"x": x, "y": y})
     .to(sprite, 1, {"scale": 1.5, "ease":EaseType.EASE_OUT_ELASTIC})
     .to(sprite, 2, {"scale": 1, "delay": 1});
```

> **NOTE:** When combining two different animations of the same property with no delay between them, the second one will overwrite the first one.

# Gameplay

## Persistency

Persistency is provided by Cocos2d-x and more specifically `CCUserDefault`.

```
var userDefaults = CCUserDefault.sharedUserDefault();
userDefaults.setIntegerForKey("polyX", x);
sprite.x = userDefaults.getIntegerForKey("polyX", 240);
```

> The persistency database can only handle simple values: boolean, integer, float, double and string.
