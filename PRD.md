# PRD — Throw Blanket Landing Page (Algeria)
**Version:** 1.0  
**Language:** Algerian Darija (دارجة)  
**Market:** Algeria (DZ)  
**Last Updated:** May 2026

---

## 1. Project Overview

A high-converting, single-product ecommerce landing page for an Algerian throw blanket brand. The page targets Algerian buyers, is fully written in Darija, and covers the complete purchase funnel — from product discovery to order confirmation — with an integrated admin panel for lead/order management.

---

## 2. Goals & Success Metrics

| Goal | Metric |
|------|--------|
| Drive purchases | Conversion rate ≥ 3% |
| Reduce drop-off | Form completion rate ≥ 60% |
| Build trust | Social proof section visible above fold on mobile |
| Operational efficiency | Admin can view/manage all orders in real time |
| WhatsApp confirmation | 100% of submitted orders trigger a WA message |

---

## 3. Target Audience

- Algerian buyers (all 58 wilayas)
- Mobile-first users (majority on Android via Facebook/Instagram)
- Arabic/Darija speakers — include French
- Impulse buyers driven by social media ads (Meta)

---

## 4. Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5 / CSS3 / Vanilla JS (single file, no framework dependency) |
| Storage | Browser localStorage + optional Firebase Realtime DB for orders |
| Admin Panel | Separate password-protected HTML page |
| Analytics | Meta Pixel (Facebook Pixel) |
| Messaging | WhatsApp Click-to-API (wa.me link with pre-filled message) |
| Hosting | Static hosting (Vercel / Netlify / cPanel) |

---

## 5. Page Sections

### 5.1 Header / Navbar
- Brand logo (uploaded by client)
- Sticky on scroll
- CTA button → scrolls to checkout
- "Stock mahdoud!" (limited stock) badge

---

### 5.2 Hero / Product Carousel
- Full-width image carousel showing all product colors and models
- Auto-play with manual navigation (dots + arrows)
- Lazy loading for performance
- Mobile swipe-enabled

**Assets needed:** All product photos 

---

### 5.3 Product Features / Why Buy
- Short punchy Darija copy
- 3–4 icons/cards: Quality, Warmth, Size options, Fast delivery
- Urgency callout: "Stock mahdoud — اطلب دروك!" (Limited stock — order now!)

---

### 5.4 Social Proof
- Grid/masonry of customer screenshot testimonials
- All client names automatically blurred/hidden (CSS filter or canvas overlay)
- Minimum 3 screenshots (client to upload more)
- Section title in Darija: "واش قالو عملاءنا"

---

### 5.5 Checkout / Order Form
The core conversion section. Fields:

| Field | Type | Details |
|-------|------|---------|
| الاسم الكامل (Full Name) | Text input | Required |
| رقم الهاتف (Phone) | Tel input | Algerian format, required |
| الولاية (Wilaya) | Dropdown | All 58 Algerian wilayas, numbered |
| الكمية (Quantity) | Number input | Min 1, default 1 |
| الحجم (Size) | Multi-checkbox | 230/235 cm → 5,000 DA / 115/235 cm → 2,500 DA |
| الموديل (Model/Color) | Multi-checkbox + image thumbnail | One or more selectable, with preview |
| **ملخص الطلب (Order Summary)** | Auto-calculated | Updates live based on size × quantity |

**Pricing logic:**
- 230/235 cm = 5,000 DA/unit
- 115/235 cm = 2,500 DA/unit
- If multiple sizes selected, total = sum of (size price × quantity)

**Submit button:** "اطلب دروك 🛒" (Order Now)

---

### 5.6 Thank You / Confirmation Screen
- Replaces form after successful submission
- Message in Darija: "شكراً على طلبك! راح نتواصلو معاك قريب"
- Order summary displayed
- WhatsApp button: sends pre-filled order details to customer's number AND notifies owner number (+213559144101)
- Meta Pixel `Purchase` event fires on submission

---

### 5.7 Footer
- Brand logo
- Social media links (Instagram, Facebook — client to provide)
- Copyright line
- Short trust message in Darija

---

## 6. Admin Panel

Separate page: `/admin.html` — password protected.

### Features:

| Feature | Description |
|---------|-------------|
| Login | Password-gated entry (hardcoded or env-based) |
| Orders Table | All submitted orders with: name, phone, wilaya, size(s), model(s), quantity, total price, date/time |
| Status Management | Mark order as: New / Confirmed / Shipped / Delivered / Cancelled |
| Filters | By wilaya, status, date range |
| Search | By name or phone |
| Export | Download orders as CSV / Excel |
| Stats Dashboard | Total orders, total revenue (DA), orders per wilaya chart, top model |
| WhatsApp shortcut | Click phone number → opens WA chat with that client |
| Delete / Archive | Soft-delete or archive old orders |

---

## 7. Meta Pixel Integration

Pixel ID: 2717020218665128  

### Events to fire:

| Event | Trigger |
|-------|---------|
| `PageView` | On page load |
| `ViewContent` | When carousel is viewed |
| `InitiateCheckout` | When user starts filling the form |
| `Purchase` | On successful form submission (with value + currency) |

---

## 8. WhatsApp Integration

### Flow:
1. Customer submits order form
2. Page fires WA `wa.me` link with pre-filled message to **owner** number (+213559144101)
3. Message includes: customer name, phone, wilaya, model(s), size(s), quantity, total price, question about the delivery home or delivery office
4. A second WA link is shown to the customer to confirm their order themselves (optional, one-tap)

### Sample owner notification message (Darija):
```
🛒 طلب جديد!
الاسم: [Name]
الهاتف: [Phone]
الولاية: [Wilaya]
الموديل: [Model(s)]
الحجم: [Size(s)]
الكمية: [Quantity]
المجموع: [Total] DA
```

---


## 10. Non-Functional Requirements

| Requirement | Detail |
|-------------|--------|
| Mobile-first | Optimized for 375px–414px screen widths |
| Page speed | LCP < 2.5s on 4G |
| RTL support | Arabic/Darija text rendered right-to-left |
| Accessibility | Sufficient color contrast, large tap targets |
| No backend required | All data stored client-side or via Firebase (no server needed) |
| Single deployable file | Landing page = one HTML file + assets folder |

---

## 11. Delivery Milestones

| Milestone | Deliverable |
|-----------|-------------|
| M1 | PRD finalized ✅ |
| M2 | Client uploads assets + provides Pixel ID |
| M3 | Landing page HTML (all sections, no real assets) |
| M4 | Assets integrated (photos, logo, social proof) |
| M5 | Admin panel built and connected |
| M6 | Meta Pixel + WhatsApp integration tested |
| M7 | Final QA + delivery |

