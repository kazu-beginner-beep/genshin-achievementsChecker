# genshin-achievementsChecker

原神 PC版のアチーブメント画面をスクリーンキャプチャし、Tesseract OCRで取得状況を検出する Windows 64-bit CLIです。

## 開発方針

- 原神のメモリ・通信・プロセスへ直接アクセスしません
- キーボード・マウス送信も行いません
- 対象解像度は 1920 x 1080 固定です
- 手動スクロールと自動キャプチャを組み合わせます

## ビルド

Windows 64-bit環境で以下を実行します。

```powershell
winget install Kitware.CMake
git clone https://github.com/microsoft/vcpkg.git
.\vcpkg\bootstrap-vcpkg.bat
.\vcpkg\vcpkg.exe integrate install
cmake -S . -B build -A x64 -DCMAKE_TOOLCHAIN_FILE="$PWD/vcpkg/scripts/buildsystems/vcpkg.cmake"
cmake --build build --config Release
```

## 実行

```powershell
.\build\Release\GenshinAchievementChecker.exe
```

実行前に原神のアチーブメント一覧を画面最上部に表示してください。
