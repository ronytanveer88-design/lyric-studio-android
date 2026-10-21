# Lyric Studio — Android APK build package

এটি আপনার আপলোড করা `lyric_studio_v4.html`-এর ভিত্তিতে তৈরি Capacitor Android wrapper ও GitHub Actions build workflow।

## কী আছে
- `www/index.html` — মোবাইল টাচ-ইন্টারফেসসহ V4 অ্যাপ এবং রেন্ডার error handling
- `package.json` — Capacitor dependency
- `capacitor.config.json` — Android app ID/name
- `.github/workflows/android-apk.yml` — GitHub Actions-এ APK build workflow

## ফোন থেকে APK বানানোর ধাপ
1. ZIP ফাইলটি Extract করুন।
2. ফোল্ডারের সব ফাইল GitHub repository-র root-এ upload করুন। root-এ `package.json`, `capacitor.config.json`, `www/`, `.github/` থাকবে।
3. GitHub repository খুলুন → **Actions** tab → **Build Android APK** workflow → **Run workflow**।
4. Build সফল হলে workflow run-এর নিচে **Artifacts** থেকে `lyric-studio-debug-apk` ZIP নামান।
5. ZIP Extract করে `app-debug.apk` ফোনে install করুন। Android চাইলে ওই উৎস থেকে install অনুমতি দিতে হবে।

## গুরুত্বপূর্ণ সীমাবদ্ধতা
- এই প্যাকেজটি APK নয়; এটি APK তৈরি করার source/build package।
- GitHub Actions-এ প্রথম build-এ Android project তৈরি হবে। dependency/workflow error হলে log দেখে ঠিক করতে হবে।
- Debug APK পরীক্ষার জন্য। Play Store-এ প্রকাশের আগে signed release build লাগবে।
- ভিডিও export MediaRecorder এবং Android WebView-এর ওপর নির্ভরশীল; সব ফোনে MP4 export নিশ্চিত নয়। রেন্ডার না চললে Chrome/Android System WebView আপডেট করে চেষ্টা করুন।
- Google Fonts অনলাইনে লোড হয়; ইন্টারনেট না থাকলে fallback Bengali font ব্যবহার হবে।
