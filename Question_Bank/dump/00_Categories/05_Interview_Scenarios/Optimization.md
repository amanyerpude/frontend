# Performance Optimization

## 📌 Web Performance Interview Question

**[Source: dump_one.md, Lines 69-136]**

### Q: How would you optimize a webpage that loads slowly due to large images?

### 🔍 Thought Process

- **Identify the bottlenecks:**
    - Large file sizes increase download time
    - Rendering gets blocked while images load
    - Multiple network requests affect performance

### 🔹 Optimization Strategies

### ✅ Image Format Optimization

```html
<!-- Use modern formats -->
<picture>
  <source srcset="hero.webp" type="image/webp">
  <source srcset="hero.avif" type="image/avif">
  <img src="hero.jpg" alt="Hero image">
</picture>
```

### ✅ Responsive Images

```html
<img
  src="small.jpg"
  srcset="small.jpg 480w, medium.jpg 800w, large.jpg 1200w"
  sizes="(max-width: 600px) 480px, (max-width: 900px) 800px, 1200px"
  alt="Responsive image"
/>
```

### ✅ Lazy Loading

```html
<img src="image.jpg" loading="lazy" alt="Lazy loaded image">
```

### ✅ CSS Optimization

```css
/* Prevent layout shift */
img {
  width: 100%;
  height: auto;
  aspect-ratio: 16/9;
}
```

### 💡 Key Takeaways

- Use **WebP/AVIF** formats for better compression
- Implement **responsive images** for different screen sizes
- Enable **lazy loading** for below-the-fold images
- Set **dimensions** to prevent layout shifts
- Use **image CDNs** for global delivery

**Pro Tip:** Use **Lighthouse** to measure Core Web Vitals and identify bottlenecks.


