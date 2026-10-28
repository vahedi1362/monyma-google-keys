# monyma-google-keys

Google's public sign-in keys (`https://www.googleapis.com/oauth2/v3/certs`), copied into
[`google_certs.json`](google_certs.json) every hour by [a GitHub Action](.github/workflows/refresh.yml).

It is a mirror for the Monyma server inside Iran, which often cannot reach Google: it checks
«ادامه با گوگل» with these keys when no other way to Google answers.

## آینه‌ی کلیدهای «ورود با گوگل»

سرورِ اصلیِ مانیما در ایران است و گوگل اغلب جوابش را نمی‌دهد. این مخزن هر ساعت کلیدهای عمومیِ گوگل
را می‌گیرد و در `google_certs.json` می‌گذارد. سرور وقتی خودش به گوگل نرسد، کلیدها را از اینجا برمی‌دارد.

در اپ کنترل: «راه‌های ورود» › «ورود با گوگل» › «ویرایش» › «پیشرفته» › «آینه‌ی کلیدهای گوگل»، یکی از این دو:

```
https://raw.githubusercontent.com/vahedi1362/monyma-google-keys/main/google_certs.json
https://cdn.jsdelivr.net/gh/vahedi1362/monyma-google-keys@main/google_certs.json
```

بعد «آزمایش اتصال به گوگل». اگر اولی از ایران باز نشد، دومی را بگذارید.

## Rules for whoever changes this repository

- **Keep it public.** GitHub Actions minutes are free and unlimited only for a public repository; that is
  the reason this repository exists apart from `monyma-server` (private), whose own job stops when the
  month's minutes run out.
- **Nothing secret here, ever.** Google's keys are public. Never add a token, a key or a server address.
- **Never edit `google_certs.json` by hand.** The Monyma server trusts these keys to check a Google
  sign-in: whoever writes this file decides who can sign in. Only the Action writes it, from Google's
  own answer.
- The file's format is the one of `server/internal/modules/auth/google_certs.json` in `monyma-server`
  (`url`, `fetched_at`, `max_age_seconds`, `keys`); the server reads its `keys` field.
