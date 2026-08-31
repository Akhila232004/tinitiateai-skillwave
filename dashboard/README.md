# Dashboard Cards

`cards.yaml` is only the dashboard index. Edit the separate template files for day-to-day content changes:

- `cards/text.yaml` for text-only slides
- `cards/image-text.yaml` for slides with an image and text
- `cards/image.yaml` for image-only slides

Supported editable fields:

- `template`: `text`, `imageText`, or `image`
- `imagePosition`: `left`, `right`, `top`, or `bottom`
- `textAlign`: `left`, `center`, or `right`
- `titleSize`, `bodySize`, `eyebrowSize`: any CSS size such as `34px` or `clamp(28px, 4vw, 52px)`
- `imageSize` and `mobileImageSize`: CSS sizes for desktop and mobile image display
- `imagePath`: repo file path, such as `design/course-icons/java.png`
- `imageUrl`: external hosted image URL

Put shared settings under `defaults`, then override them on any topic or slide.
