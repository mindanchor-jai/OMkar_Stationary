# Omkar Loyalty Coupons — Two Pages + GitHub

| File | Purpose | Where it lives |
|---|---|---|
| `index.html` | The page customers see | GitHub repo (published link) |
| `data.json` | Anonymous coupon progress shown on the page | GitHub repo (updated automatically by Admin) |
| `Admin.html` | The shop's tool | **Shop computer only. Do not upload.** |

## How the Admin page reaches the public page

All customer data (names, phones, tokens, purchases) is stored only in the browser on the shop device where `Admin.html` is opened. When you press **Publish now** (or automatically after changes, if enabled), Admin sends one small file, `data.json`, directly to your GitHub repository using a limited token. `index.html` reads that file. Customers see updates 1–2 minutes later (GitHub's refresh time).

`data.json` contains only: shop name, target, reward text, and for each coupon the code, purchase count, status and valid-till date. Never names, phones, tokens or history.

## One-time setup

1. Create a GitHub repository. Upload `index.html` and `data.json` to the root.
2. Repo **Settings → Pages → Deploy from branch → main / (root)**. Public link: `https://<user>.github.io/<repo>/`
3. Create a token: GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token. Repository access: **Only select repositories** → your repo. Permissions → **Contents: Read and write**. Set expiry (e.g. 1 year).
4. Save `Admin.html` in a fixed folder on the shop computer. Open it → **Publish & Backup → GitHub connection**: enter username, repository, branch (main) and the token → Save → Test connection. Optionally tick automatic publishing.
5. Admin → Settings: shop name, purchases needed (default 10), reward text, reward cost, validity (default 12 months).
6. Test with sample coupons, then Publish & Backup → Erase everything, and publish.

Always open `Admin.html` from the same folder and browser: browser storage is tied to it.

## Daily use

- **Issue coupon**: name + mobile. One active coupon per number. Valid 1 year.
- **Record purchase**: code + Record (or +1 in the list).
- **Reward**: at the target a token screen opens; "Send via WhatsApp" opens a private message. Tokens can be shown again or reissued.
- **Redeem**: Redeem reward → code + token → Verify → Mark as redeemed. A repeat attempt shows ALREADY REDEEMED.
- **Corrections**: History → Void (reason required); everything stays in Activity.
- A yellow banner appears when the public page is out of date.

## Security notes

- The token can only edit files in that one repository. It is stored in the shop browser only and is **not** included in backups. If the device is lost, delete the token on GitHub.
- `data.json` is public by design (same data customers see).
- Manual fallback: Publish & Backup → Manual option → Download data.json → upload it to GitHub yourself.

## Backups (important)

Data is stored only in this browser. Use **Download backup (JSON)** at least weekly and keep it private (it contains names, phones and tokens). **Restore backup** recovers or moves data. Use one device for admin; devices do not sync.

## Excel

Publish & Backup → **Export for Excel (CSV)**: Coupons, Purchases, Rewards & cost.

## Limits

- Coupons can be passed on; the system prevents duplicate redemption, not transfer.
- Tested with a simulated GitHub connection, not yet against your real repository: do the setup test (step 6) before going live.
