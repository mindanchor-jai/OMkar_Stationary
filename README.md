# Omkar Loyalty Coupons — Simple Two-File Setup

No servers, no Google, no PIN. Two files:

| File | Purpose | Where it lives |
|---|---|---|
| `index.html` | The page customers see | **Uploaded to GitHub — the only published file** |
| `Admin.html` | The shop's tool: coupons, purchases, tokens, redemptions | **Stays on the shop computer. Never upload it.** |

## How it works

All customer data (names, phones, tokens, purchases) lives **only in the browser on the shop device where `Admin.html` is opened**. The admin file contains no data and is not published anywhere.

To update the public page:
1. Open `Admin.html` → **Publish & Backup** → **Download index.html**.
2. GitHub repo → **Add file → Upload files** → upload it (same name replaces the old one) → Commit.
3. The public page updates in a minute or two.

The downloaded `index.html` contains only anonymous coupon codes, purchase counts, status and valid-till dates.

## First-time setup

1. Create a GitHub repository and upload `index.html` only.
2. Repo **Settings → Pages → Deploy from branch → main / (root)**.
3. Public link (share in WhatsApp): `https://<user>.github.io/<repo>/`
4. Save `Admin.html` in a fixed folder on the shop computer and always open it from there (double-click). Browser storage is tied to that file location and browser, so don't move it or switch browsers. Bookmark it.
5. Admin → Settings: shop name, purchases needed (default 10), reward text, reward cost, validity (default 12 months).
6. Test, then clear test data: Publish & Backup → Erase everything.

## Daily use

- **Issue coupon**: name + mobile number. One active coupon per number. Valid 1 year from issue date.
- **Record purchase**: type code and press Record (or +1 in the list).
- **Reward**: at the target the token screen opens. "Send via WhatsApp" opens a private pre-filled message. Tokens can be shown again or reissued.
- **Redeem**: Redeem reward → code + token → Verify → Mark as redeemed. A second attempt shows ALREADY REDEEMED.
- **Corrections**: History → Void (reason required). Voided entries stay visible with the reason, plus the Activity log.
- A yellow banner shows when the public page is out of date or no backup exists.

## IMPORTANT: backups

Data is stored only in this browser. Clearing browser data, moving the file, a new device or a reinstall can lose it. Use **Download backup (JSON)** at least weekly and keep the file private (names, phones, tokens inside). **Restore backup** brings everything back or moves it to another device. Use one device for admin; devices do not sync.

## Excel records

Publish & Backup → **Export for Excel (CSV)**: Coupons, Purchases, Rewards & cost. Paste into your Excel workbook.

## Limits

- Customers see changes only after you upload a new `index.html`.
- Coupons can be passed on; the system prevents duplicate redemption, not transfer.
