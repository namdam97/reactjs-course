# Week 1: HTML & CSS Basics

## 🎯 Mục tiêu tuần này

- Hiểu semantic HTML
- Nắm vững Box Model
- Tạo layout với Flexbox
- Responsive design cơ bản

## 📁 Files

- `index.html` - HTML structure với semantic tags
- `styles.css` - CSS styling với Flexbox và responsive design

## 🚀 Cách chạy

### Cách 1: Mở trực tiếp
```bash
# Mở file trong browser
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows
```

### Cách 2: Dùng Live Server (Recommended)
1. Install VS Code extension: **Live Server**
2. Right-click vào `index.html`
3. Chọn "Open with Live Server"
4. Website sẽ tự động reload khi bạn sửa code!

### Cách 3: Simple HTTP Server
```bash
# Python 3
python -m http.server 8000

# Node.js (nếu đã cài npx)
npx serve

# Sau đó mở: http://localhost:8000
```

## 📝 Bài tập thực hành

### Bài 1: Thêm Skills Section
Thêm một section mới giữa About và Contact:

```html
<section id="skills" class="skills">
    <h2>My Skills</h2>
    <div class="skills-grid">
        <div class="skill-card">
            <h3>Backend</h3>
            <ul>
                <li>Golang</li>
                <li>REST APIs</li>
                <li>Databases</li>
            </ul>
        </div>
        <div class="skill-card">
            <h3>Learning</h3>
            <ul>
                <li>HTML & CSS</li>
                <li>JavaScript</li>
                <li>React</li>
            </ul>
        </div>
    </div>
</section>
```

**Nhiệm vụ CSS:**
- Dùng Flexbox hoặc Grid cho `.skills-grid`
- Style `.skill-card` với background, padding, border-radius
- Responsive: 2 columns trên desktop, 1 column trên mobile

### Bài 2: Cải thiện Navigation
- Thêm hamburger menu cho mobile
- Thêm smooth scroll khi click nav links
- Active state cho nav link hiện tại

### Bài 3: Thêm Cards với Flexbox
Tạo một section "Projects" với card layout:

```html
<section class="projects">
    <h2>My Projects</h2>
    <div class="cards-container">
        <article class="card">
            <img src="https://via.placeholder.com/300x200" alt="Project 1">
            <h3>Project Title</h3>
            <p>Project description goes here...</p>
            <a href="#" class="btn">View Project</a>
        </article>
        <!-- Repeat 2 more times -->
    </div>
</section>
```

**Yêu cầu CSS:**
- Flexbox layout: 3 cards per row
- Hover effect trên cards
- Responsive: 1 card per row trên mobile

## 🎨 Styling Challenges

### Challenge 1: Color Scheme
Thay đổi color scheme của website:
- Chọn palette từ [Coolors.co](https://coolors.co/)
- Thay thế tất cả colors trong CSS
- Maintain good contrast (text readable)

### Challenge 2: Typography
- Thử các Google Fonts khác nhau
- Tạo typography scale (h1, h2, h3, p)
- Ensure readability (line-height, letter-spacing)

### Challenge 3: Animations
Thêm CSS transitions/animations:
```css
.card {
    transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}
```

## 📚 Concepts được sử dụng

### HTML
- ✅ Semantic tags: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- ✅ Form elements: `<form>`, `<input>`, `<textarea>`, `<button>`, `<label>`
- ✅ Lists: `<ul>`, `<li>`
- ✅ Links: `<a>`

### CSS
- ✅ **Box Model**: margin, padding, border
- ✅ **Flexbox**: display: flex, justify-content, align-items, gap
- ✅ **Positioning**: sticky navigation
- ✅ **Colors**: background, gradients
- ✅ **Typography**: font-family, font-size, line-height
- ✅ **Transitions**: smooth hover effects
- ✅ **Responsive**: @media queries
- ✅ **Pseudo-classes**: :hover, :focus, :active

## 🔍 Inspect & Learn

### Browser DevTools Tips
1. **Right-click → Inspect** bất kỳ element nào
2. **Elements tab**: Xem HTML structure
3. **Styles panel**: Xem CSS được áp dụng
4. **Toggle device toolbar** (Cmd+Shift+M): Test responsive
5. **Edit CSS trực tiếp** trong DevTools để experiment

### CSS Box Model
```
Inspect bất kỳ element nào và xem Box Model visualization:
┌─────────────────────────────┐
│         Margin              │
│  ┌─────────────────────┐    │
│  │      Border         │    │
│  │  ┌───────────────┐  │    │
│  │  │   Padding     │  │    │
│  │  │  ┌─────────┐  │  │    │
│  │  │  │ Content │  │  │    │
│  │  │  └─────────┘  │  │    │
│  │  └───────────────┘  │    │
│  └─────────────────────┘    │
└─────────────────────────────┘
```

## ✅ Checklist

### HTML
- [ ] Sử dụng semantic HTML tags
- [ ] Form có labels và proper attributes
- [ ] Mọi image có alt text
- [ ] HTML validates (https://validator.w3.org/)

### CSS
- [ ] Dùng `box-sizing: border-box`
- [ ] Responsive trên mobile, tablet, desktop
- [ ] Hover states cho interactive elements
- [ ] Colors có good contrast
- [ ] Font sizes readable

### General
- [ ] Code indented properly
- [ ] CSS organized by sections
- [ ] Comments để explain sections
- [ ] Tested trên Chrome, Firefox, Safari

## 🎯 Next Steps

Sau khi hoàn thành Week 1:
1. ✅ Complete all exercises above
2. 📸 Screenshot website của bạn
3. 🚀 Deploy lên GitHub Pages hoặc Netlify
4. 📝 Move to Week 2: Portfolio Project

## 💡 Tips

### 1. Write HTML first, CSS later
Xây dựng structure trước, style sau.

### 2. Use browser DevTools extensively
Experiment trực tiếp trong browser.

### 3. Mobile-first approach
Viết CSS cho mobile trước, sau đó thêm @media cho larger screens.

### 4. Keep it simple
Đừng over-complicate. Focus on fundamentals.

### 5. Validate your code
Use W3C validators to check for errors.

## 🆘 Common Issues & Solutions

### Issue 1: Styles không apply
**Solution:**
- Check CSS file được link đúng trong HTML
- Check spelling của class names
- Check CSS syntax errors
- Hard refresh (Cmd+Shift+R)

### Issue 2: Flexbox không work
**Solution:**
- Verify `display: flex` on parent
- Check flex-direction
- Inspect in DevTools

### Issue 3: Responsive không work
**Solution:**
- Add viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Check @media query syntax
- Use DevTools device toolbar to test

## 🔗 Resources

- [MDN HTML Reference](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [Flexbox Froggy](https://flexboxfroggy.com/) - Learn Flexbox through game
- [CSS-Tricks Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

---

**Happy Coding! 🚀**

Nếu stuck, tham khảo:
- [QUICK_REFERENCE.md](../QUICK_REFERENCE.md) - CSS Flexbox cheat sheet
- [RESOURCES.md](../RESOURCES.md) - Learning resources

