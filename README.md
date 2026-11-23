# ✨ Baby World BD — Premium WhatsApp Order Manager

WhatsApp Cloud API webhook-based order-management console with emoji-rich menus, order collection, moderator access, search, edit, notes, reports, activity logs and guarded Steadfast booking.

## 🚀 Deploy on Render (Web Service)
1. Extract ZIP and upload the complete `babyworld-bd-premium-whatsapp` folder to a GitHub repository.
2. Render → **New + → Web Service** → select your repository.
3. Build command: `npm install` | Start command: `npm start`.
4. Add environment variables from `.env.example` in Render's Environment tab. Set `DATA_DIR=/var/data`.
5. Attach Render Persistent Disk with mount path `/var/data`.
6. Deploy. Copy the HTTPS service URL.
7. Meta Developer App → WhatsApp → Configuration: Webhook URL `https://YOUR-RENDER-URL/webhook`; Verify Token must match `VERIFY_TOKEN`. Subscribe to `messages`.
8. Test with an order first; verify API and courier response before booking real parcels.

## 🔐 Environment variables
See `.env.example`. Never share API tokens. Admin/moderator phone numbers must be entered with country code (digits only, e.g. Bangladesh `8801...`).

## 💬 Moderator commands
- 🧭 `MENU` / `HELP`
- 📦 `ALL`, 🕒 `PENDING`, ✅ `CONFIRMED`, 🚚 `BOOKED`, 🏁 `DELIVERED`, ↩️ `RETURNED`, 🚫 `CANCELLED`, ⚠️ `FAILED`, 📮 `QUEUE`
- ➕ `ADD`, 🔍 `SEARCH <ID/phone/name>`, 📲 `CONFIRM <ID>`, 🔁 `RETRY <ID>`, ✏️ `EDIT <ID>`, 🔄 `STATUS <ID> <status>`, 📝 `NOTE <ID>`, 🛑 `CANCEL <ID>`
- 📊 `REPORT`, 🗓️ `REPORT WEEK`, 📤 `EXPORT`, 🧾 `LOG` (Admin only)

## ⚠️ Production notes
JSON-file storage is suitable only for a single instance. Before production use, implement webhook signature validation, rate limits, database persistence and additional idempotency safeguards. Moderator notification delivery may require each moderator to initiate the WhatsApp chat. Cloud API and Steadfast credentials/response fields must be tested. Booking is triggered by moderator `CONFIRM`/`RETRY` commands only. Export is currently a text snippet, not a file attachment.
