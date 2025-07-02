# 🟢 Gumroad.com Performance Benchmark

This file documents the Lighthouse benchmark results of [Gumroad.com](https://gumroad.com), used for comparison against [Slayd.in](https://slayd.in) in the web performance audit.

---

## 📱 Mobile Audit Results

| Metric                  | Value      | Status |
|-------------------------|------------|--------|
| Performance Score       | 71         | 🟡 Fair |
| Accessibility           | 87         | 🟡 Fair |
| Best Practices          | 100        | 🟢 Good |
| SEO                     | 92         | 🟢 Good |
| First Contentful Paint  | 3.2s       | 🟡 Slight Delay |
| Largest Contentful Paint| 6.1s       | 🔴 Needs Improvement |
| Total Blocking Time     | 10ms       | 🟢 Excellent |
| Speed Index             | 3.5s       | 🟡 Okay |
| Cumulative Layout Shift | 0.036      | 🟢 Excellent |

📌 **Notes:**
- Mobile performance is decent, with fast interactivity and low layout shift.
- The main area for improvement is LCP (6.1s), which slightly delays visual completeness.

---

## 💻 Desktop Audit Results

| Metric                  | Value      | Status |
|-------------------------|------------|--------|
| Performance Score       | 100        | 🟢 Excellent |
| Accessibility           | 87         | 🟡 Fair |
| Best Practices          | 100        | 🟢 Excellent |
| SEO                     | 92         | 🟢 Good |
| First Contentful Paint  | 0.6s       | 🟢 Excellent |
| Largest Contentful Paint| 0.6s       | 🟢 Excellent |
| Total Blocking Time     | 30ms       | 🟢 Excellent |
| Speed Index             | 0.9s       | 🟢 Excellent |
| Cumulative Layout Shift | 0.007      | 🟢 Excellent |

📌 **Notes:**
- Gumroad's desktop performance is nearly perfect.
- Near-instant load and paint metrics.
- Clean execution with excellent optimization across all areas.

---

## 📸 Screenshots

See `/assets/gumroad/` for original Lighthouse screenshots of both Mobile and Desktop audits.

---

**Test Date:** July 2, 2025  
**Tool Used:** Lighthouse 
**Tester:** Siddharth Narela
