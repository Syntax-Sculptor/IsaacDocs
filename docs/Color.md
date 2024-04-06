---
tags:
  - Globals
  - Class
---
# Class "Color"
## Constructors
### Color () {: aria-label='Constructors' }
[ ](#){: .rep .tooltip .badge }
#### [Color](Color.md) Color ( float R, float G, float B, float A = 1, float RO = 0, float GO = 0, float BO = 0 ) {: .copyable aria-label='Constructors' }

Constructor for the "Color" class.

When using the [Font](Font.md) class, use [KColor()](KColor.md) instead.

Colors are made of three separate components, tint, colorize and offset. Tint acts like a color multiplicator. Offset is a color which is added after the tint is applied. Colorize is complicated. See the `:::lua SetColorize()` function for a detailed description.

R, G, B, A, RO, GO and BO accept numbers between 0 and 1.
___
## Operators
### __mul () {: aria-label='Operators' }
[ ](#){: .abrep .tooltip .badge }
#### [Color](Color.md) __mul ( [Color](Color.md) right ) {: .copyable aria-label='Operators' }

Defines the multiplication of two [Color](Color.md) objects using the `*` operator.
___
## Constants
### Color.Default {: aria-label='Constants' }
[ ](#){: .rep .tooltip .badge }

Equivalent to `:::lua Color(1, 1, 1, 1)`, the color white.
___
## Functions
### Lerp () {: aria-label='Functions' }
[ ](#){: .static .tooltip .badge } [ ](#){: .abrep .tooltip .badge }
#### static [Color](Color.md) Lerp ( [Color](Color.md) c1, [Color](Color.md) c2, float t ) {: .copyable aria-label='Functions' }

Returns a new color by blending two existing colors (`c1` and `c2`) based on `t`. `t` is a ratio between 0 and 1 which determines the position between the two colors, where 0 corresponds to `c2` and 1 corresponds to `c2`. For example, having `t` be 0.5 would return a color exactly in the middle of `c1` and `c2`.
___
### Reset () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void Reset ( ) {: .copyable aria-label='Functions' }

Resets the color back to the default color, `:::lua Color(1, 1, 1, 1)`, which is white.
___
### Set·Colorize () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void SetColorize ( float Red, float Green, float Blue, float Amount ) {: .copyable aria-label='Functions' }

The colorize function can be used to change the color of sprites. Its the best for that purpose, since it does not affect existing color animations like the flashing of creep.

The values can be between 0 and 1 for normal coloration. if you use higher numbers the color gets more vibrant.

???- note "Notes"
    The alpha component determines how much colorization must be applied. The function takes the original color, converts it to grayscale, multiplies it by the RGB components and then blends it back with the original color. The alpha value determines the blending factor.
    Colorization is applied after the tint and before the offset function.

???- example "Example Code"
    - `:::lua SetColorize(1, 1, 1, 1)` will turn the sprite into grayscale.
    - `:::lua SetColorize(1, 0, 0, 1)` will turn it red but not as a red tint but as shades of red.
    - `:::lua SetColorize(1, 1, 1, 2)` will invert the sprite without touching its luminosity.

    This code changes the color of red Creep to be purple
    ```lua
    mod:AddCallback(ModCallbacks.MC_POST_EFFECT_INIT, function(_, effect)
      if effect.Variant == EffectVariant.CREEP_RED then
        local color = Color(1, 1, 1, 1, 0, 0, 0)
        color:SetColorize(4, 0, 4, 1)
        local sprite = effect:GetSprite()
        sprite.Color = color
      end
    end)
    ```
___
### Set·Offset () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void SetOffset ( float RedOffset, float GreenOffset, float BlueOffset ) {: .copyable aria-label='Functions' }

Sets the color's offset. The offset is a color that's added to the sprite after its tint was applied.
___
### Set·Tint () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void SetTint ( float RedTint, float GreenTint, float BlueTint, float AlphaTint ) {: .copyable aria-label='Functions' }

Sets the color's tint. The tint acts like a color multiplier.
___
## Variables
### A {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float A  {: .copyable aria-label='Variables' }
Alpha value of the color, where 0 is fully transparent, 1 is fully opaque.
___
### B {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float B  {: .copyable aria-label='Variables' }
Blue value of the color. Number between 0 and 1.
___
### BO {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float BO  {: .copyable aria-label='Variables' }
Blue-Offset value of the color. Number can be positive or negative.

___
### G {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float G  {: .copyable aria-label='Variables' }
Green value of the color. Number between 0 and 1.

___
### GO {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float GO  {: .copyable aria-label='Variables' }
Green-Offset value of the color. Number can be positive or negative.

___
### R {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float R  {: .copyable aria-label='Variables' }
Red value of the color. Number between 0 and 1.

___
### RO {: aria-label='Variables' }
[ ](#){: .abrep .tooltip .badge }
#### float RO  {: .copyable aria-label='Variables' }
Red-Offset value of the color. Number can be positive or negative.
