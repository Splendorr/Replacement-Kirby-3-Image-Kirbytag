# Replacement Kirby 3 (image:) Kirbytag that re-encodes all displayed images to fix iPhone rotation and save bandwidth

Overrides built-in `(image:)` Kirbytag. Keeps all normal functionality as of [Kirby 3.2.2](https://github.com/getkirby/kirby/blob/3.2.2/config/tags.php#L79-L144), while re-encoding all displayed images in Kirbytext fields to make sure they have the correct orientation, and optionally compress to a maximum width to save bandwidth.

**The problem:** Photos uploaded from iOS can appear incorrectly rotated in many major browsers (Chrome, Firefox, Safari on Mac), because they use EXIF data for rotation that isn't parsed automatically. This plugin applies Kirby's built-in thumb() processor to re-encode images as JPEG with minimal loss in quality. It can also 

## Usage:

Download and place the folder in your Kirby project's `site/plugins` folder. Works out of the box with all uploaded image files displayed with the `(image:)` Kirbytag. Optionally set options listed below in `site/config/config.php`.

## Options

You can change options in `/site/config/config.php`:
```php
return [
  // Maxwidth defaults to 2000px wide. Set to a large number like 10000 if you want to always display your images at their original resolution
  'splendorr.imagetag.maxwidth' => 2000,
  // Quality defaults to 90%. I found that setting it to 100 results in files that are twice the size of the original iOS photo, while the default of 90 produces a slightly-smaller file at the same dimensions without visible compression artifacts.
  'splendorr.imagetag.quality' => 90,
];
```
