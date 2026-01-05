# Руководство по удалению белого фона с изображений 25-40.png

Белый фон на изображениях 25-40.png можно удалить несколькими способами:

## ✅ ВАРИАНТ 1: Онлайн сервис (САМЫЙ ПРОСТОЙ)

### remove.bg - Бесплатно для небольших изображений
1. Перейдите на https://www.remove.bg/
2. Загрузите каждое изображение (25.png - 40.png)
3. Скачайте обработанные файлы
4. Замените оригинальные файлы в папке `/Users/elizavetakulbabenko/Downloads/01/`

### Adobe Express - Бесплатный онлайн редактор
1. Перейдите на https://www.adobe.com/express/feature/image/remove-background
2. Загрузите изображения
3. Скачайте с прозрачным фоном

## ✅ ВАРИАНТ 2: Установка ImageMagick (РЕКОМЕНДУЕТСЯ)

### Установка через Homebrew
```bash
# Установите Homebrew если еще нет
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Установите ImageMagick
brew install imagemagick

# Запустите скрипт для обработки
cd /Users/elizavetakulbabenko/Downloads/01
./process_images.sh
```

### После установки ImageMagick можно обработать все изображения автоматически:
```bash
cd /Users/elizavetakulbabenko/Downloads/01

# Обработка каждого изображения
for i in {25..40}; do
  magick "${i}.png" -fuzz 15% -transparent white "${i}.png"
  echo "✓ Обработан ${i}.png"
done
```

## ✅ ВАРИАНТ 3: Ручная обработка в Preview (macOS)

Для каждого файла 25-40.png:
1. Откройте изображение в Preview (Просмотр)
2. Нажмите на значок инструмента выделения (кнопка разметки)
3. Выберите "Instant Alpha" из меню инструментов
4. Кликните на белый фон и перетащите для выделения
5. Нажмите Delete
6. Сохраните файл (⌘S)

## ✅ ВАРИАНТ 4: Photopea (Бесплатный онлайн Photoshop)

1. Перейдите на https://www.photopea.com/
2. Откройте изображение (File → Open)
3. Выберите Magic Wand Tool (W)
4. Кликните на белый фон
5. Нажмите Delete
6. File → Export As → PNG
7. Сохраните с прозрачностью

## После обработки изображений:

1. Замените обработанные файлы в папке проекта
2. Закоммитьте изменения:
```bash
cd /Users/elizavetakulbabenko/Downloads/01
git add 25.png 26.png 27.png 28.png 29.png 30.png 31.png 32.png 33.png 34.png 35.png 36.png 37.png 38.png 39.png 40.png
git commit -m "Remove white background from product images 25-40"
git push origin main
```

3. Можно также удалить CSS mix-blend-mode из index.html (строки 2536-2562), так как он больше не нужен

---

**Примечание:** CSS решение (mix-blend-mode) было применено как временное, но для идеального результата рекомендуется физически удалить белый фон с изображений одним из способов выше.
