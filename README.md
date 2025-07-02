# 🧪 Web Performance Audit Report — Slayd.in

## 📍 Overview

This report provides a comprehensive audit of [Slayd.in](https://slayd.in), a digital marketplace, evaluating its technical performance, user experience, and areas for optimization. The audit includes benchmark comparisons against [Gumroad.com](https://gumroad.com), a well-optimized marketplace, to better contextualize Slayd.in’s current performance metrics.

---

## 🔎 Tools & Methodology

- **Lighthouse (v12.6.1)** in Chrome DevTools for both Mobile and Desktop views
- **PageSpeed Insights** for mobile-first performance review
- **UX heuristics** and manual walkthrough for user flow evaluation
- **Side-by-side comparison** with Gumroad.com using Lighthouse metrics

---

## 📱 UX Observations

| Section          | Observations |
|------------------|--------------|
| **Homepage**     | The main banner takes too long to appear, especially on mobile. There is no loading feedback while data is being fetched. |
| **Navigation**   | The mobile menu is slightly delayed in response and lacks fluidity. Desktop navigation is smoother. |
| **Product Cards**| Images often pop into view late. There's a visible layout shift in some cases, which may affect perceived trust. |
| **Checkout**     | The flow appears functional but lacks visual cues that make the user feel “safe” or guided, especially during network delays. |

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

📌 **Key Pain Points**:
- **LCP and FCP are significantly delayed**, especially on mobile.
- **Desktop TBT (760ms)** suggests heavy JavaScript blocking interactivity.
- **Speed Index** is very high (bad) — visible content takes too long to stabilize.

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

🟩 Gumroad exhibits excellent performance, particularly in Desktop view with a perfect score of 100 and nearly instantaneous paint metrics.

---

## 📈 Performance Comparison Table

| Metric                  | **Slayd.in (Mobile)** | **Gumroad (Mobile)** | **Slayd.in (Desktop)** | **Gumroad (Desktop)** |
|-------------------------|------------------------|------------------------|------------------------|------------------------|
| Performance Score       | 33                     | 71                     | 59                     | 100                    |
| First Contentful Paint  | 7.3s                   | 3.2s                   | 1.4s                   | 0.6s                   |
| Largest Contentful Paint| 13.7s                  | 6.1s                   | 3.6s                   | 0.6s                   |
| Total Blocking Time     | 40ms                   | 10ms                   | 760ms                  | 30ms                   |
| Speed Index             | 12.2s                  | 3.5s                   | 4.2s                   | 0.9s                   |
| CLS                     | 0.022                  | 0.036                  | 0.013                  | 0.007                  |

✅ **Conclusion**: Gumroad is highly optimized, and serves as a model for both frontend performance and code efficiency. Slayd.in requires urgent attention to image delivery, JavaScript execution, and layout stability.

---

## 🛠️ Key Issues Identified

| Area        | Problem Description | Impact |
|-------------|---------------------|--------|
| LCP Delay   | Hero images load too late (13.7s on mobile) | Slow perceived load time |
| Image Size  | Images not compressed or lazy loaded | Bandwidth-heavy | 
| JS Bundle   | Large JS bundle blocking main thread | Interactivity delay |
| Cache Policy| No long-term caching for static assets | Re-fetching resources |
| CLS         | Slight layout shift due to delayed image rendering | Poor user experience |

---

## ✅ Prioritized Recommendations

| Priority | Issue | Recommendation | Technical Notes |
|----------|-------|----------------|-----------------|
| 🔴 High  | Largest Contentful Paint too high | Preload above-the-fold images + convert to WebP | Use `<link rel="preload">`, Next.js `<Image priority>` |
| 🔴 High  | JS Blocking on Desktop | Code-splitting + tree-shaking | Implement dynamic imports via React.lazy / Next.js |
| 🟡 Medium| No caching policy | Enable `Cache-Control` headers for static assets | Configure server or CDN (e.g., Cloudflare) |
| 🟡 Medium| CLS on image loads | Set width/height attributes or CSS aspect-ratio | Prevent layout shifts |
| 🟢 Low   | SEO best practices already good | No change needed | Keep monitoring |

---

## 🔄 Suggested Optimizations

- Implement **lazy loading** and **image compression (WebP/AVIF)**.
- Use **Next.js `getStaticProps`** and `ISR` to cache product pages.
- Optimize third-party scripts and audit for **unused dependencies**.
- Add **skeleton UI or shimmer loaders** for perceived speed.

---

## 📎 Attachments & Artifacts

- 📂 `/assets/`: Contains all screenshots from Lighthouse and PageSpeed
- 📝 `comparison/gumroad-audit.md`: Includes raw notes from Gumroad benchmark
- 📄 `slayd-audit-report.pdf`: This Markdown converted into styled PDF for final submission

---

## 📌 Final Thoughts

Slayd.in is functional and has the core structure of a modern marketplace but suffers from clear performance inefficiencies, particularly on mobile. Improving load performance and responsiveness will significantly enhance user satisfaction, SEO rankings, and overall retention — and help position Slayd.in as a fast, trustworthy platform in a competitive space.

---

**Prepared by:**  
`Siddharth Narela`  
`Performance Audit for Internship Assignment – July 2025`  
