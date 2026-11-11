# Казахмедимпорт — готовые сборки приложения

Этот репозиторий — только для распространения собранных версий приложения
учёта оборудования (Android APK и Windows-сборка). Исходный код и
резервные копии данных здесь **не** хранятся — они в приватном репозитории
[`service_center_app`](https://github.com/kazmedimport-bot/service_center_app).

Репозиторий публичный специально, чтобы ссылка на скачивание работала у
любого человека без аккаунта GitHub.

## Как скачать

Зайти на вкладку **[Releases](../../releases)** → выбрать последнюю
версию → скачать нужный файл:

- `*.apk` — для установки на Android (разрешить установку из
  неизвестных источников при первом запуске);
- `*-windows.zip` — для Windows (распаковать и запустить `.exe` внутри
  папки).

## Как опубликовать новую версию (для разработчика)

```powershell
flutter build apk --no-tree-shake-icons
flutter build windows --no-tree-shake-icons
Compress-Archive -Path "build\windows\x64\runner\Release\*" -DestinationPath "service_center_app-windows.zip" -Force

gh release create vX.Y `
  "build\app\outputs\flutter-apk\app-release.apk" `
  "service_center_app-windows.zip" `
  --repo kazmedimport-bot/service_app_realese `
  --title "vX.Y" `
  --notes "Что изменилось"
```
