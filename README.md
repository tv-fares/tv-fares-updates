# TV فارس Glass — قناة التحديثات العامة

هذا المستودع مخصص لنشر ملفات APK الموقعة ومعلومات تحديث التطبيق فقط. **كود TV فارس وأسرار التوقيع في مشروع آخر خاص ولا تُنشر هنا.**

## الحالة الحالية

- قناة التحديثات: `https://raw.githubusercontent.com/tv-fares/tv-fares-updates/main/latest.json`
- `status: pending` — **ما فيه APK موقّع ومنشور بعد**.
- مشغل التلفزيون لا يستعمل manifest جاهز حتى ينشر نظام البناء الخاص إصدارًا موثوقًا.
- عندما تُجهز الأسرار في المشروع الخاص ويُشغّل workflow `Publish signed TV Fares update`، ينشر APK الموقّع أولاً ثم يستبدل هذا الملف ببيانات حقيقية متحقق منها، مثل:
```json
{
  "channel": "stable",
  "status": "ready",
  "packageName": "sa.personal.oootv.glass",
  "versionCode": 13,
  "versionName": "1.3-cinematic-glass",
  "apkUrl": "https://github.com/tv-fares/tv-fares-updates/releases/download/v1.3/tv-fares-glass-v1.3.apk",
  "sha256": "<actual checksum from published signed APK>",
  "signerSha256": "<actual signing certificate digest>"
}
```
المثال ليس إصداراً متاحًا للتثبيت ولا يصلح استعمال قيمه كمعلومات إصدار فعلية.

التطبيق يفحص البيانات مرة يوميًا عند فتحه، ويرفض الاختلاف في البصمة ورقم الإصدار وشهادة التوقيع. التثبيت على Android TV لا يتم بصمت؛ يجب موافقة المستخدم.

**لا ترفع keystore أو كلمات مرور أو توكنات أو كود المصدر إلى هذا المستودع العام.**
