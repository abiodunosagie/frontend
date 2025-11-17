# Lesson 5: Images & Media

> **"A picture is worth a thousand words. Learn to use them properly."**

---

## 🖼️ The `<img>` Tag

**Images make websites visual.**

**Syntax:**
```html
<img src="path-to-image.jpg" alt="Description of image">
```

**Required attributes:**
- `src` = Source (path to image file)
- `alt` = Alternative text (describes image for screen readers and when image fails to load)

---

## 🎯 Image File Types

| Format | Use For | Pros | Cons |
|--------|---------|------|------|
| **JPG/JPEG** | Photos | Small file size | Lossy compression |
| **PNG** | Graphics, logos, transparency | Lossless, supports transparency | Larger files |
| **GIF** | Simple animations | Small, animated | Limited colors (256) |
| **SVG** | Icons, logos | Scalable, tiny file size | Not for photos |
| **WebP** | Modern alternative | Smaller than JPG/PNG | Older browser support |

---

## 🎨 Basic Image Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Images Demo</title>
</head>
<body>
  <h1>My Photo Gallery</h1>

  <!-- Local image (in same folder) -->
  <img src="photo.jpg" alt="Sunset over mountains">

  <!-- Image from URL -->
  <img src="https://picsum.photos/400/300" alt="Random placeholder image">
</body>
</html>
```

---

## 📐 Image Sizing

### Using HTML Attributes

```html
<img src="photo.jpg" alt="Photo" width="400" height="300">
```

**Pros:** Simple
**Cons:** Fixed size, not responsive

### Using CSS (BETTER)

```html
<style>
  img {
    max-width: 100%;  /* Never wider than container */
    height: auto;     /* Maintain aspect ratio */
  }
</style>

<img src="photo.jpg" alt="Photo">
```

**This makes images responsive!**

---

## 🎨 Responsive Images

```html
<style>
  .responsive-img {
    width: 100%;       /* Fill container */
    max-width: 600px;  /* But not larger than this */
    height: auto;      /* Keep aspect ratio */
  }
</style>

<img src="photo.jpg" alt="Photo" class="responsive-img">
```

---

## 🖼️ Image as Link

```html
<a href="gallery.html">
  <img src="thumbnail.jpg" alt="View gallery">
</a>
```

Clicking the image navigates to `gallery.html`.

---

## 🎯 Alt Text Best Practices

**Alt text is critical for:**
- Screen readers (blind users)
- When images fail to load
- SEO (search engines)

### Good Alt Text:

```html
<!-- Descriptive -->
<img src="dog.jpg" alt="Golden retriever playing fetch in a park">

<!-- Informative -->
<img src="chart.jpg" alt="Bar chart showing 50% increase in sales from 2023 to 2024">

<!-- Empty for decorative images -->
<img src="decorative-line.png" alt="">
```

### Bad Alt Text:

```html
<!-- Too vague -->
<img src="dog.jpg" alt="image">
<img src="dog.jpg" alt="photo">

<!-- Redundant -->
<img src="dog.jpg" alt="Image of a dog">  <!-- Don't say "image of" -->
```

---

## 🎨 Figure and Figcaption

**Semantic way to add captions:**

```html
<figure>
  <img src="sunset.jpg" alt="Sunset over ocean">
  <figcaption>Beautiful sunset at Santa Monica Beach, 2024</figcaption>
</figure>
```

```css
figure {
  margin: 20px 0;
  text-align: center;
}

figcaption {
  font-style: italic;
  color: #666;
  margin-top: 10px;
}
```

---

## 📁 Image File Paths

### Same folder:
```
my-site/
  ├── index.html
  └── photo.jpg
```
```html
<img src="photo.jpg" alt="Photo">
```

### Subfolder:
```
my-site/
  ├── index.html
  └── images/
      └── photo.jpg
```
```html
<img src="images/photo.jpg" alt="Photo">
```

### Parent folder:
```
my-site/
  ├── photo.jpg
  └── pages/
      └── about.html
```
```html
<!-- In about.html -->
<img src="../photo.jpg" alt="Photo">
```

---

## 🎥 Video Element

```html
<video width="640" height="360" controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Your browser doesn't support video.
</video>
```

**Attributes:**
- `controls` - Show play/pause/volume controls
- `autoplay` - Start playing automatically (annoying, avoid!)
- `loop` - Repeat video
- `muted` - Start muted
- `poster` - Thumbnail image before playing

---

## 🎵 Audio Element

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser doesn't support audio.
</audio>
```

---

## 📺 Embedding YouTube Videos

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>
```

**How to get YouTube embed code:**
1. Go to YouTube video
2. Click "Share"
3. Click "Embed"
4. Copy the `<iframe>` code

---

## 🎨 Styled Image Gallery

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Gallery</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background-color: #f5f5f5;
    }

    h1 {
      text-align: center;
      margin-bottom: 30px;
      color: #333;
    }

    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .gallery-item {
      background: white;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      transition: transform 0.3s;
    }

    .gallery-item:hover {
      transform: translateY(-5px);
    }

    .gallery-item img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      display: block;
    }

    .gallery-item figcaption {
      padding: 15px;
      text-align: center;
      color: #666;
    }
  </style>
</head>
<body>
  <h1>My Photo Gallery</h1>

  <div class="gallery">
    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=1" alt="Random photo 1">
      <figcaption>Photo 1</figcaption>
    </figure>

    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=2" alt="Random photo 2">
      <figcaption>Photo 2</figcaption>
    </figure>

    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=3" alt="Random photo 3">
      <figcaption>Photo 3</figcaption>
    </figure>

    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=4" alt="Random photo 4">
      <figcaption>Photo 4</figcaption>
    </figure>

    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=5" alt="Random photo 5">
      <figcaption>Photo 5</figcaption>
    </figure>

    <figure class="gallery-item">
      <img src="https://picsum.photos/400/300?random=6" alt="Random photo 6">
      <figcaption>Photo 6</figcaption>
    </figure>
  </div>
</body>
</html>
```

**Copy this and run it!** It's a fully functional responsive gallery.

---

## 🖼️ Background Images (CSS)

```html
<style>
  .hero {
    background-image: url('hero-bg.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
</style>

<div class="hero">
  <h1>Welcome to Our Site</h1>
</div>
```

---

## ✏️ Practice Exercise

Create `images-practice.html`:

1. Add three images with proper alt text
2. Make one image a link
3. Create a figure with image and caption
4. Make all images responsive (max-width: 100%)
5. Add a background image to a div

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Images Practice</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      max-width: 800px;
      margin: 0 auto;
    }

    img {
      max-width: 100%;
      height: auto;
      border-radius: 8px;
    }

    figure {
      margin: 20px 0;
      text-align: center;
    }

    figcaption {
      margin-top: 10px;
      font-style: italic;
      color: #666;
    }

    .bg-section {
      background-image: url('https://picsum.photos/1200/400');
      background-size: cover;
      background-position: center;
      height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
      margin: 30px 0;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h1>Image Practice</h1>

  <h2>Regular Images</h2>
  <img src="https://picsum.photos/600/400?random=1" alt="Random landscape photo">

  <h2>Image as Link</h2>
  <a href="https://unsplash.com" target="_blank">
    <img src="https://picsum.photos/600/400?random=2" alt="View more photos on Unsplash">
  </a>

  <h2>Figure with Caption</h2>
  <figure>
    <img src="https://picsum.photos/600/400?random=3" alt="Beautiful mountain landscape">
    <figcaption>Mountain landscape captured at sunrise</figcaption>
  </figure>

  <h2>Background Image</h2>
  <div class="bg-section">
    <h2>Hero Section with Background</h2>
  </div>
</body>
</html>
```

</details>

---

## 🐛 Common Mistakes

### 1. **Missing alt attribute**
```html
<!-- Wrong -->
<img src="photo.jpg">

<!-- Right -->
<img src="photo.jpg" alt="Description of photo">
```

### 2. **Wrong file path**
```html
<!-- Wrong (file is in images/ folder) -->
<img src="photo.jpg" alt="Photo">

<!-- Right -->
<img src="images/photo.jpg" alt="Photo">
```

### 3. **Not making images responsive**
```html
<!-- Fixed width breaks on mobile -->
<img src="photo.jpg" width="800" alt="Photo">

<!-- Responsive -->
<style>
  img { max-width: 100%; height: auto; }
</style>
<img src="photo.jpg" alt="Photo">
```

---

## 🎯 Key Takeaways

1. **`<img>` tag** requires `src` and `alt`
2. **Alt text is mandatory** (accessibility and SEO)
3. **Make images responsive** with `max-width: 100%` and `height: auto`
4. **Use `<figure>` and `<figcaption>`** for semantic captions
5. **File paths matter** (same folder, subfolder, parent folder)
6. **`object-fit: cover`** for consistent image sizes in grids
7. **Optimize images** (compress before uploading)

---

## 🚀 Next Lesson

Now you can add images. Next, learn **lists** - one of the most common HTML structures!

**Next:** [Lesson 6: Lists →](./06-lists.md)

---

**Images make websites beautiful. Use them wisely, optimize them well, and always add alt text.** 🖼️
