# AGENTS.md — Throw Blanket Landing Page (Algeria)

## Project Type
Static HTML/CSS/JS site — no build system, no frameworks, no tests.

## Key Files
- `index.html` — Main landing page (to be created)
- `admin.html` — Password-protected admin panel (to be created)
- `images/` — Logo, product photos, testimonials
- `PRD.md` — Product requirements (source of truth)

## Developer Commands
No build commands needed. Edit files directly and open in browser.

## Important Conventions
- **Language:** Algerian Darija (RTL support required)
- **Pricing:** 230/235cm = 5,000 DA, 115/235cm = 2,500 DA
- **Wilayas:** All 58 Algerian wilayas must be in dropdown
- **Meta Pixel ID:** 2717020218665128
- **WhatsApp Owner:** +213559144101
- **Storage:** localStorage + optional Firebase for orders
- **Mobile-first:** Optimize for 375px–414px screens

## Admin Panel Features
- Password-gated login
- Orders table with: name, phone, wilaya, size, model, quantity, total, date
- Status: New / Confirmed / Shipped / Delivered / Cancelled
- Filters: wilaya, status, date range
- Search: by name or phone
- Export: CSV/Excel download
- Stats dashboard: total orders, revenue, orders per wilaya chart
- WhatsApp shortcut: click phone to open chat

## WhatsApp Integration
1. On order submit: fire wa.me link to owner (+213559144101) with pre-filled order details
2. Show customer a second wa.me link to confirm their order
3. Message format in Darija:
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

## Meta Pixel Events
- `PageView` — on page load
- `ViewContent` — when carousel viewed
- `InitiateCheckout` — when user starts form
- `Purchase` — on form submission (with value + currency DZD)

## Deployment
Static hosting: Vercel / Netlify / cPanel. Single deployable HTML file + assets folder.