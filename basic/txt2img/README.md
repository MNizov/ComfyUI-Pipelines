# Base_TXT2IMG (SD1.5/SDXL)

Базовый пайплайн для генерации изображений по текстовому описанию (Text-to-Image). Поддерживает модели SD1.5 и SDXL.

## Описание работы пайплайна

Пайплайн реализует стандартный процесс генерации изображения из текстового описания:

1. **Загрузка модели** — CheckpointLoaderSimple загружает базовую модель (чекпоинт), содержащую MODEL (для генерации), CLIP (для кодирования текста) и VAE (для декодирования изображения)
2. **Кодирование промптов** — два CLIPTextEncode преобразуют позитивный и негативный текстовые промпты в условные векторы (CONDITIONING)
3. **Подготовка латентного пространства** — EmptyLatentImage создает пустой латентный тензор заданного разрешения
4. **Сэмплирование** — KSampler выполняет итеративный процесс денойзинга, используя модель, CONDITIONING и пустой латент
5. **Декодирование** — VAEDecode преобразует полученный латентный тензор в итоговое изображение (IMAGE)
6. **Сохранение** — SaveImage сохраняет сгенерированное изображение на диск

## Используемые ноды (переменные для настройки)

### CheckpointLoaderSimple
Загрузчик базовой модели. Определяет стилистику и качество генерации.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `ckpt_name` | Название файла чекпоинта | `RealVisXL_V5.0_Lightning_fp16.safetensors` |

### CLIPTextEncode (позитивный)
Преобразует текстовое описание желаемого изображения в условный вектор.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `text` | Позитивный промпт | `(masterpiece, best quality:1.2), ultra detailed, 8k, photorealistic, cinematic lighting, soft shadows, warm atmosphere, cozy mood, 1girl, solo, beautiful face, captivating green eyes, full red lips, long dark hair, wearing a cozy sweater, sitting in an old library, reading a book, surrounded by bookshelves, soft sunlight streaming through a window, dust particles in the air, comfortable armchair, elegant, intellectual, calm, focused, peaceful expression` |

### CLIPTextEncode (негативный)
Преобразует текстовое описание нежелательных элементов в условный вектор.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `text` | Негативный промпт | `blurry, low quality, cartoon, painting, illustration, anime, sketch, watermark, text, ugly, deformed, oversaturated, bad anatomy, extra fingers, fused fingers, mutation, bad proportions, cropped, worst quality, jpeg artifacts, out of frame` |

### EmptyLatentImage
Создает пустой латентный тензор для начала генерации.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `width` | Ширина изображения (пиксели) | `512` (для SD1.5), `1024` (для SDXL) |
| `height` | Высота изображения (пиксели) | `512` (для SD1.5), `1024` (для SDXL) |
| `batch_size` | Количество изображений за запуск | `1` |

### KSampler
Основной сэмплер, выполняющий процесс денойзинга.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `seed` | Сид генерации (для воспроизводимости) | `291194128237493` или `randomize` |
| `steps` | Количество шагов генерации | `30` |
| `cfg` | Масштаб классификатора (влияет на следования промпту) | `7` |
| `sampler_name` | Алгоритм сэмплирования | `dpmpp_2m` |
| `scheduler` | Расписание шума | `karras` |
| `denoise` | Сила денойзинга (1.0 для полной генерации) | `1` |

### VAEDecode
Декодирует латентный тензор в изображение. Не требует настройки.

### SaveImage
Сохраняет итоговое изображение в папку `ComfyUI/output`.

| Поле | Описание | Пример значения |
|------|----------|-----------------|
| `filename_prefix` | Префикс имени файла | `ComfyUI` |

## Быстрый старт

1. Загрузите пайплайн в ComfyUI (файл `Base_TXT2IMG (SD1.5SDXL).json`)
2. В ноде `CheckpointLoaderSimple` укажите путь к вашему чекпоинту
3. При необходимости отредактируйте позитивный и негативный промпты
4. Настройте разрешение в `EmptyLatentImage` (512x512 для SD1.5, 1024x1024 для SDXL)
5. Нажмите "Queue Prompt" для генерации
6. Результат появится в папке `ComfyUI/output`