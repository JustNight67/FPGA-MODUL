# Example using Assets Directory

## Advantages:

- Hugo can process and optimize images
- Better performance with image resizing
- Can generate multiple sizes (responsive images)
- Better caching

## Usage Example:

### Basic usage:

```markdown
{{ $image := resources.Get "images/briefing/gambar-b1.png" }}
<img src="{{ $image.RelPermalink }}" alt="Time Sharing System" class="img-fluid w-100">
```

### With image processing:

```markdown
{{ $image := resources.Get "images/briefing/gambar-b1.png" }}
{{ $resized := $image.Resize "800x" }}
<img src="{{ $resized.RelPermalink }}" alt="Time Sharing System" class="img-fluid w-100">
```

### With multiple sizes (responsive):

```markdown
{{ $image := resources.Get "images/briefing/gambar-b1.png" }}
{{ $small := $image.Resize "400x" }}
{{ $medium := $image.Resize "800x" }}
{{ $large := $image.Resize "1200x" }}

<img src="{{ $medium.RelPermalink }}" 
     srcset="{{ $small.RelPermalink }} 400w,
             {{ $medium.RelPermalink }} 800w,
             {{ $large.RelPermalink }} 1200w"
     sizes="(max-width: 400px) 400px, (max-width: 800px) 800px, 1200px"
     alt="Time Sharing System" 
     class="img-fluid w-100">
```
