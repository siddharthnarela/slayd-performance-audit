# 🧪 Web Performance Audit Report — Slayd.in

## 📍 Overview

This report provides a comprehensive performance and user experience audit of [Slayd.in](https://slayd.in), a digital product marketplace. The goal is to assess technical performance, uncover UX friction points, and compare performance benchmarks against a leading marketplace — [Gumroad.com](https://gumroad.com). The audit outlines measurable metrics, visual diagnostics, and actionable recommendations.

---

## 🔎 Tools & Methodology

- **Lighthouse** in Chrome DevTools (Mobile and Desktop modes)
- **PageSpeed Insights** for mobile-first performance testing
- **Manual UX Walkthrough** on mobile, tablet, and desktop
- **Benchmark Comparison** with Gumroad.com

---

## 📱 UX Observations

| Area               | Observation |
|--------------------|-------------|
| **Image Scaling**   | Showcase images are excessively large, dominating screen real estate and reducing content discoverability. This leads to a cluttered, overwhelming homepage UX. |
| **Scroll Behavior** | A persistent horizontal scrollbar appears on certain screen widths and overlaps the main content, particularly on the homepage. This is distracting and suggests layout breakpoints are misconfigured. |
| **Product Page Layout** | After clicking a product, the product details page opens in a narrow, scrollable column that resembles a mobile view. On desktop and tablet screens, this layout appears underutilized and awkward. |
| **Responsiveness** | The UI appears to be designed mobile-first, but lacks fluid adaptation for larger screens — making it feel constrained and unoptimized on desktops. |
| **Navigation**     | Mobile navigation is slightly delayed and lacks smooth transitions. Desktop menu works well. |
| **Search Latency** | Search functionality suffers from noticeable delays in fetching results, impacting the overall flow and responsiveness of product discovery. |
| **Checkout Flow**  | Functionally complete but lacks feedback states (e.g. loading spinners), which may create uncertainty during transactions. |

---

## 📊 Lighthouse Audit Results

### 🚀 Slayd.in

| Metric                  | **Mobile**      | **Desktop**     |
|-------------------------|------------------|------------------|
| Performance Score       | 33               | 59               |
| Accessibility           | 88               | 88               |
| Best Practices          | 75               | 78               |
| SEO                     | 100              | 100              |
| First Contentful Paint  | 7.3s             | 1.4s             |
| Largest Contentful Paint| 13.7s            | 3.6s             |
| Total Blocking Time     | 40ms             | 760ms            |
| Speed Index             | 12.2s            | 4.2s             |
| Cumulative Layout Shift | 0.022            | 0.013            |

📌 **Key Issues:**
- Extremely high **LCP** on mobile due to large unoptimized images
- JavaScript blocking delays interactivity on Desktop
- High **Speed Index** indicates content takes time to fully render
- Minimal CLS, but layout instability still observed from images

---

### 🟢 Gumroad.com (Benchmark)

| Metric                  | **Mobile**      | **Desktop**     |
|-------------------------|------------------|------------------|
| Performance Score       | 71               | 100              |
| Accessibility           | 87               | 87               |
| Best Practices          | 100              | 100              |
| SEO                     | 92               | 92               |
| First Contentful Paint  | 3.2s             | 0.6s             |
| Largest Contentful Paint| 6.1s             | 0.6s             |
| Total Blocking Time     | 10ms             | 30ms             |
| Speed Index             | 3.5s             | 0.9s             |
| Cumulative Layout Shift | 0.036            | 0.007            |

🟩 Gumroad exhibits ideal optimization, especially on Desktop with a perfect 100 score and near-instant paint and interactivity metrics.

---

## 📈 Performance Comparison Table

| Metric                  | **Slayd.in (Mobile)** | **Gumroad (Mobile)** | **Slayd.in (Desktop)** | **Gumroad (Desktop)** |
|-------------------------|------------------------|------------------------|------------------------|------------------------|
| Performance Score       | 33                     | 71                     | 59                     | 100                    |
| First Contentful Paint  | 7.3s                   | 3.2s                   | 1.4s                   | 0.6s                   |
| Largest Contentful Paint| 13.7s                  | 6.1s                   | 3.6s                   | 0.6s                   |
| Total Blocking Time     | 40ms                   | 10ms                   | 760ms                  | 30ms                   |
| Speed Index             | 12.2s                  | 3.5s                   | 4.2s                   | 0.9s                   |
| Cumulative Layout Shift | 0.022                  | 0.036                  | 0.013                  | 0.007                  |

✅ **Conclusion**: Gumroad provides a smooth, fast, and responsive user experience across devices. Slayd.in, while functional, needs targeted improvements in image handling, layout structure, and interactivity to reach similar performance levels.

---

## 🛠️ Key Issues Identified

| Area        | Description | Impact |
|-------------|-------------|--------|
| LCP Delay   | Hero images take over 13s to appear on mobile | Poor perceived speed |
| Image Size  | Oversized images without compression or lazy loading | Slow load, high data usage |
| Scrollbar Conflict | Horizontal scrollbar overlays images | Visual bugs on various screens |
| Mobile-Centric Layout | Product pages are limited to mobile-width scrolling | Poor experience on tablets/desktops |
| Search Latency | Slow search results | Hurts usability and engagement |
| JS Bundle   | Heavy scripts blocking main thread | Lag in UI responsiveness |
| No Caching  | Static assets reloaded on every visit | Poor repeat load times |
| Feedback Gaps | No loading indicators in product or checkout flow | User uncertainty and friction |

---

## ✅ Prioritized Recommendations

| Priority | Issue | Recommendation | Technical Notes |
|----------|-------|----------------|-----------------|
| 🔴 High  | Large LCP | Compress and lazy-load hero/product images | Use WebP, `next/image`, `loading="lazy"` |
| 🔴 High  | JS Blocking (Desktop) | Code-splitting and tree-shaking | Use React.lazy or dynamic import with Next.js |
| 🔴 High  | Search Delay | Debounce input and optimize API | Add loading state + cache results |
| 🟡 Medium| Scrollbar overlay | Fix layout overflow & breakpoints | `overflow-x: hidden`, layout refactor |
| 🟡 Medium| Product page scaling | Make layout responsive on larger viewports | Use flex/grid with media queries |
| 🟡 Medium| No caching | Add cache headers via CDN or server | Set Cache-Control headers |
| 🟢 Low   | CLS issues | Define static dimensions for images | Use CSS `aspect-ratio` or fixed height |
| 🟢 Low   | Missing UX feedback | Add loading spinners / skeletons | Use animated placeholders for perceived performance |

---

## 🔄 Suggested Optimizations

- Use **Image CDNs** (e.g. ImageKit, Cloudflare) for optimized delivery
- Add **skeleton loaders** to improve perceived speed
- Audit and remove **unused CSS/JS**
- Apply **responsive design best practices** across screen sizes
- Cache API responses and static assets for faster repeated use

---

## 📎 Included Files

- `slayd-audit-report.md` – This report
- `/assets/` – Lighthouse and PageSpeed screenshots
- `gumroad-benchmark.md` – Audit metrics for Gumroad
- `slayd-audit-report.pdf` – Printable PDF version (optional)

---

## 🧠 Final Thoughts

Slayd.in is a promising platform but currently underperforms in areas that directly impact user satisfaction and retention. Focused optimization on image delivery, layout responsiveness, and JavaScript execution will significantly enhance the user experience — especially for mobile-first users — and better align the product with modern web performance standards.

---

**Prepared by:**  
`Siddharth Narela`  
Performance Audit for Internship Assignment – July 2025
