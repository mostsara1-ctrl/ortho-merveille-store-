<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

- Admin-managed products, banner, and contact information live in the Cloud database (products, store_settings) and load into StoreProvider via public read server functions; writes go through admin-session-checked server functions and update state only after the server confirms, so every visitor sees the same store and failed saves never appear saved.
- Admin image uploads use shared quality preparation: keep originals unless oversized, then resize with high smoothing; store privately and serve via /api/public/images/<file>.
- The store starts empty; legacy demo book ids are filtered out, and books saved earlier only in a browser's LocalStorage are uploaded once when the admin signs in on that browser.
- Storefront editing uses StoreProvider edit-mode and editor selection state with shared accessible modal forms; reuse the product form in the dashboard to keep both editing paths consistent.
- Admin authorization uses server-verified credentials and an encrypted HTTP-only session; neither localStorage roles nor edit flags grant access, and every managed save revalidates that session.
- Visitor password recovery uses Cloud Auth email links and the public reset-password route; validate the recovery identity before showing the password form and never send current_password for recovery updates.
- Visitor login suppresses credential autofill with optional CSS password masking and form-scoped autofill/restoration clearing; never use read-only locks or alter account/session storage to clear visible fields.
- Login and logout refresh StoreProvider's verified admin status before replacing the current route; LocalStorage only mirrors status, so routing and storefront controls stay synchronized without granting forged access.
- Normalize legacy ordered product images into explicit cover and gallery fields on read; all product displays use the cover, and details combine cover with gallery.
- Homepage covers use description_style.coverFrame and shared CSS for preview/storefront; blurFill adds the same cover as a blurred backdrop, stretch fills without cropping; originals stay unchanged.
- Keep checkout calculations and wilaya fee selection in the shared pure checkout-pricing module so checkout and WhatsApp use the same tested rules; per-wilaya office/home fees live in store_settings JSON, never fall back to retired global fees, and null means pending rather than free.
- Use shared cartLines for the badge, drawer, checkout and reminder so missing or hidden saved books never create phantom cart counts; preserve stored items and raw removal indexes.

- Store customization, including optional workPhotos, uses the shared validated schema and store_settings JSON; defaults remain unchanged, content stays plain text/images, and saves use the verified admin session and private image-upload pipeline.
- Photo layouts use workPhotoLayouts/bannerLayout; optional bannerStyle preserves legacy banner fit/corners. Use photoFrameCss for visible-image rounding in contain mode; preserve originals/indexes.
- Optional per-book video URLs live in description_style.video; uploads require the encrypted admin session, use the private product-videos bucket, and streaming proxies verify a visible book references the file (or a verified admin) before forwarding range requests.
- Admin settings are grouped in AdminSettingsPortal, opened from the dashboard header; reuse existing forms and server-confirmed saves to avoid duplicate settings paths and preserve storefront behavior.
- Order creation re-fetches visible products, coupon rules and delivery settings server-side, snapshots prices, and uses hashed high-entropy guest access tokens; private order/file/coupon tables have no browser grants, and only verified admin sessions can manage them.
- PDF files stay in the private book-pdfs bucket; entitlement is checked against manually confirmed non-cancelled orders before issuing a 60-second download URL. Customer submission never implies payment.
- Optional operations use a shared validated schema with disabled/empty defaults; coupons apply to books after the existing quantity discount, while free delivery compares the pre-discount book subtotal strictly above the configured threshold.
- Advanced settings remain in operations JSON and are disabled by default; shared wholesale pricing runs before quantity/coupon/reward discounts, and pre-order information is snapshotted on order lines.
- Reviews require a verified customer identity, remain pending until an encrypted-session-verified admin approves them, and public reads expose only approved reviews for visible books.
- Loyalty uses server-verified customer identities and immutable order snapshots; a row-locking database trigger reserves redemption, earns points only on confirmed payment, and reverses effects on cancellation without duplicate credits.
- Sales reports aggregate all persisted orders behind the admin session and exclude unpaid/cancelled orders from revenue; abandoned-cart reminders are on-site only (CartReminder, toggle in advanced settings); email reminders would require a separate consent-based marketing provider, never managed app emails.
- Owner-written storefront text is auto-translated (AI) into French/English after admin saves and cached in store_translations keyed by source text; displays use StoreProvider tx() while admin forms keep the original text.
- Product QR codes use the published public storefront URL, never the current admin/preview origin, so printed codes can be opened by customers without editor access.
- Payment QR images are owner-uploaded originals in operations JSON through the private image pipeline; never synthesize bank QR payloads or bypass receipt/manual payment confirmation. Packaging QR cards use the public status-only tracking lookup, never guest PDF access tokens.
- Keep cart-click feedback in the shared cart-motion helper and mount OrderConfetti only in the server-confirmed checkout success view; both respect reduced motion and the owner's animation-off setting without changing payment state.

- Photo and book collage uploads share PhotoCollageEditor: retain selected source files for live layout previews and add only the confirmed result through existing saves; canvas contains and clips each whole photo to its cell to prevent overlap.
