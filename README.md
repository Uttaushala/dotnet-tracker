# Трекер курса .NET (Android)

Приложение-обёртка: внутри чек-лист (`app/src/main/assets/index.html`) и весь учебный материал курса (`app/src/main/assets/content.js`), читается без интернета.
Прогресс хранится на телефоне. В разделе «Дни» есть резервная копия: текстом, без серверов.

## Как получить APK

### Способ 1. Android Studio (на этом компьютере)
1. Установи Android Studio (с JDK 17 внутри).
2. File → Open → выбери эту папку. Дождись синхронизации Gradle.
3. Build → Build APK(s). Файл появится в `app/build/outputs/apk/debug/app-debug.apk`.
4. Скопируй `app-debug.apk` на телефон и открой его. Разреши установку из этого источника.

### Способ 2. Из командной строки
Нужны JDK 17 и Android SDK (переменная `ANDROID_HOME`).
```
gradlew.bat assembleDebug
```
APK: `app\build\outputs\apk\debug\app-debug.apk`.

### Способ 3. GitHub Actions
```
git init
git add .
git commit -m "Tracker app"
git branch -M main
git remote add origin https://github.com/<твой-логин>/dotnet-tracker.git
git push -u origin main
```
Во вкладке Actions дождись зелёной сборки «Build APK» и скачай артефакт `tracker-apk`.

## Обновление списка заданий
Правь `app/src/main/assets/index.html` (массив `WEEKS` в начале скрипта) и собирай заново. Прогресс при обновлении поверх старой версии сохраняется.
