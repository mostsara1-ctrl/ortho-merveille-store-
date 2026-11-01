# Admin functionality
- [ ] Repair collage layout selection in both photo and book uploads, preview changes before adding, and verify all four arrangements without changing stored content.
- [x] Preserve image clarity on new uploads without redesigning covers or changing stored images; 33 tests pass and real-browser readFiles retains a 1800×1200 PNG byte-for-byte; existing homepage images load unchanged. Older compressed photos require re-uploading originals.
- [x] Refine all nine existing owl illustrations and header logo; update matching public icons, preserve image paths and store layout; all eleven homepage owl instances load, desktop/mobile verified without runtime errors, build OK.
- [x] Add whole-cover filled-frame and stretch modes to shared cover editor/rendering; authenticated save/reload verified for both on a real book, original fit restored; four cover tests pass.
- [x] Fix rounded corners and rounding amount on homepage photos: rounding now applies to the visible whole image; admin save/read-back verified for 24px, 80px and straight; original 96px restored.
- [x] Add banner width, height, shape, size, fit and adjustable straight/rounded corners; admin save and homepage 800×400 with 24px, 80px and straight verified; original banner restored.
- [x] Restore Photos title inside settings only; shared preset and pixel width/height controls verified with photo 640×480 and banner 800×300 after save/reload, no homepage title; original banner restored and test photo removed, 18 related tests pass.
- [x] Remove the owner photo title; per-image orientation, custom proportions and display width saved and read back after reload, test photo removed.
- [x] Add optional uploaded explanatory video per book; admin upload/save, public WebM playback, byte-range 206, reload, gallery viewing, other-book absence and removal verified. MP4 delivered successfully but local Chromium lacks its playback codec. All 127 tests pass.
- [x] Add independent optional owner-with-products photos; authenticated upload/save and homepage rendering/reload verified, temporary photos removed and empty section absent; 23 related tests pass.
- [x] Repair false checkout save-failure from blocked WhatsApp navigation; existing saved order/receipt confirmed, same order replay shows success in sandbox and opens the correct WhatsApp URL outside popup restrictions. No duplicate order created; 16 checkout tests pass.
- [x] Add subtle cart-click motion and success-only confetti, preserving payment confirmation and motion preferences; real-book cart click and isolated confetti rendering verified, success/failure checkout tests pass. No real payment/order was submitted.
- [x] Keep visitor fields available while removing silent DOM prefilling before the next paint; manual input, deletion, visibility and silent/delayed prefilling verified, 15 login tests pass.
- [x] Investigate visitor credential prefilling: no app credential source found; clear DOM-restored and delayed autofill, discourage password-manager detection without read-only locks. Browser editing/visibility/restoration checks and 14 tests pass; the user's browser autofill provider cannot be inspected here.
- [x] Ensure visitor and admin passwords support deleting and correcting characters; Backspace/Delete verified on both live login pages and 10 related tests pass.
- [x] Show only covers on homepage and retain clicked galleries (real books verified in browser); add saved cover framing controls in the shared editor (schema and submit tests pass; owner-session save/reload not exercised).
- [x] Add visitor password visibility, recovery prompt after three incorrect passwords, and public email reset page; real browser verified visibility and three failures, tests cover reset requests and password updates. Email delivery/link round-trip not exercised.
- [x] Add optional owner-uploaded BaridiMob QR to checkout, preserving mandatory receipt and manual confirmation; original bank QR must be supplied by the owner in payment settings.
- [x] Add printable thank-you QR cards and a public tracking page using existing status-only lookup; checked guest page and existing tracking dialog, with automated code lookup coverage.
- [x] Add moderated reviews, confirmed-sales reports, pre-order controls, loyalty rewards, wholesale pricing, and a public FAQ page in the existing settings portal.
- [x] Verify authenticated portal tabs and FAQ save/read-back/reload/removal; all 60 tests pass, including pricing and review approval/security rules. No test content remains.
- [ ] Abandoned-cart email reminders: requires a dedicated marketing email service; not permitted through built-in app emails.
- [x] Persist checkout orders and provide protected admin order/status management.
- [x] Add optional threshold-based free delivery and configurable percentage/fixed coupons with shared tested pricing.
- [x] Add book visibility and private PDF upload/payment-gated delivery.
- [x] Add WhatsApp link, welcome text, and owner biography/photo controls in settings.
- [x] Verify settings, orders, pricing, visibility, and PDF security end-to-end; all 52 tests pass and temporary data removed.
- [ ] Send paid PDF links automatically by email: blocked until the owner configures a verified sending email domain; secure on-site downloads already work after manual payment confirmation.
- [x] Consolidate all settings into a top tools-button portal and verify authenticated access, all tabs, existing saves, reload, and mobile fit.
- [x] Add secure online appearance/visibility settings with unchanged defaults.
- [x] Add owner-managed text/image sections with add, reorder, hide, and delete controls.
- [x] Verify settings save, storefront read-back, refresh, and restore original settings.
# Checkout pricing
- [x] Replace global fees with blank office/home fee inputs for every wilaya; verified real admin save/reload/restoration and tested checkout selection, pending fees, and WhatsApp totals.
- [x] Add owner-editable desk/home fees; update checkout totals and show unset fees as pending.
- [x] Add book quantity controls and an add-book catalog link.
- [x] Apply 15% discount for three or more books and include the breakdown in WhatsApp.
- [x] Test pricing and WhatsApp submission with isolated inputs; verify real-book checkout quantities, discount, refresh, admin fee save/read-back and restoration in the browser.

- [x] Persist banner and multi-image product uploads with visible failure handling.
- [x] Save all product fields, including zero prices and optional old price.
- [x] Add live, persistent phone, email, and address settings in the existing design.
- [x] Test saved changes through the storefront and after refresh.

# Direct storefront editing
- [x] Add permanent edit-mode switch without login restrictions.
- [x] Connect banner, book add/edit/delete, and footer controls to modal forms.
- [x] Verify storefront edits and refresh persistence end-to-end.

# Secure admin and product fixes
- [x] Replace public edit mode with secure admin login and password visibility control.
- [x] Separate cover/gallery uploads while preserving existing product images.
- [x] Verify saved prices, format switching, image browsing, and denied unauthenticated access.

# Admin login repair
- [x] Keep login fields empty and validate exact credentials server-side.
- [x] Synchronize admin access immediately and redirect after login.
- [x] Preserve verified access after refresh without trusting browser flags.
- [x] Verify login, editing, refresh, rejected credentials, and logout.

# Category shimmer and writing icon
- [x] Add a slow, continuous shimmer sweep over the homepage category icons.
- [x] Add an owl icon for the writing (Écriture) category.
- [x] Verify both in the preview without changing any other store element.
