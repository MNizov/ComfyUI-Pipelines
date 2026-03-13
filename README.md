# 🎨 ComfyUI Pipelines Collection

Коллекция профессиональных пайплайнов для **ComfyUI**, разработанных для решения различных задач генерации и редактирования изображений.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![ComfyUI](https://img.shields.io/badge/ComfyUI-2.0.0+-blue)](https://github.com/comfyanonymous/ComfyUI)

## 📋 Оглавление
- [О себе](#-о-себе)
- [Особенности](#-особенности)
- [Быстрый старт](#-быстрый-старт)
- [Требования](#-требования)
- [Установка плагинов](#-установка-плагинов)
- [Модели](#-модели)
- [Пайплайны](#-пайплайны)
- [Лицензия](#-лицензия)
- [Контакты](#-контакты)

## 👨‍💻 О себе

Опыт в ComfyUI:
- 🧩 Разработки кастомных нод
- 🎯 Интеграции SAM, ControlNet, IP-Adapter
- ⚡ Оптимизации под SDXL и Lightning-модели
- 🏗️ Построения пайплайнов

## 🚀 Особенности

### ✅ Что внутри

| Раздел | Техники | Статус |
|--------|---------|--------|
| **Basic** | TXT2IMG, IMG2IMG, Hires Fix | ✅ Готово |
| **ControlNet** | Canny, Depth | ✅ Готово |
| **IP-Adapter** | Стиль + лицо | ✅ Готово |
| **Inpainting** | SAM + YOLO, ControlNet Inpaint | ✅ Готово |
| **LoRA** | Стилизация | ✅ Готово |

### ✅ Ключевые особенности

- 📁 **Каждый пайплайн в отдельной папке** — JSON, README и примеры вместе
- 🖼️ **Примеры результатов** для каждого workflow
- 📝 **Подробная документация** на русском языке
- 🎯 **Оптимизировано под RealVisXL V5.0 Lightning**
- 🔧 **Рабочие обходные пути** (без проблемных зависимостей)

## 🚀 Быстрый старт

1. **Установите ComfyUI** (если ещё нет) — [официальный репозиторий](https://github.com/comfyanonymous/ComfyUI)
2. **Установите ComfyUI Manager** (рекомендуется) — через `git clone` или по [инструкции](https://github.com/ltdrdata/ComfyUI-Manager)
3. **Установите необходимые плагины** (см. раздел ниже)
4. **Скачайте модели** и положите в соответствующие папки
5. **Выберите нужный пайплайн** в папке
6. **Загрузите JSON** в ComfyUI (перетащите файл в окно)
7. **Нажмите Queue Prompt** и наслаждайтесь результатом 🎉

## 🛠️ Требования

### Необходимые плагины

Установите через ComfyUI Manager или вручную:

| Плагин | Ссылка | Для чего |
|--------|--------|----------|
| **ComfyUI-Impact-Pack** | [GitHub](https://github.com/ltdrdata/ComfyUI-Impact-Pack) | SAM, детекторы |
| **ComfyUI-Impact-Subpack** | [GitHub](https://github.com/ltdrdata/ComfyUI-Impact-Subpack) | YOLO-детекторы |
| **comfyui_controlnet_aux** | [GitHub](https://github.com/Fannovel16/comfyui_controlnet_aux) | Препроцессоры ControlNet |
| **ComfyUI-IPAdapter-Plus** | [GitHub](https://github.com/cubiq/ComfyUI_IPAdapter_plus) | IP-Adapter |
| **ComfyUI-VideoHelperSuite** | [GitHub](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite) | Для видео (опционально) |

### Системные требования

- **GPU:** NVIDIA с 8-12+ GB VRAM (для SDXL)
- **RAM:** 16+ GB
- **ОС:** Windows / Linux / macOS
- **Python:** 3.10+

## 📥 Модели

### Основные модели

| Модель | Назначение | Ссылка | Куда положить |
|--------|------------|--------|---------------|
| **RealVisXL V5.0 Lightning** | Базовая модель для SDXL | [Hugging Face](https://huggingface.co/SG161222/RealVisXL_V5.0_Lightning) | `models/checkpoints/` |
| **SAM ViT-B** | Сегментация объектов | [Facebook](https://dl.fbaipublicfiles.com/segment_anything/sam_vit_b_01ec64.pth) | `models/sams/` |
| **YOLO-детекторы** | Поиск объектов | Автоматически скачиваются | `models/ultralytics/` |

### ControlNet модели (для SDXL)

| Модель | Ссылка | Куда положить |
|--------|--------|---------------|
| Canny | [Hugging Face](https://huggingface.co/diffusers/controlnet-canny-sdxl-1.0) | `models/controlnet/` |
| Depth | [Hugging Face](https://huggingface.co/diffusers/controlnet-depth-sdxl-1.0) | `models/controlnet/` |
| Inpaint | [Hugging Face](https://huggingface.co/destitech/controlnet-inpaint-dreamer-sdxl) | `models/controlnet/` |

## 📌 Важные замечания

- ⚠️ **GroundingDINO не используется** — из-за проблем совместимости с transformers. Детекция работает через YOLO (UltralyticsDetectorProvider)
- 🎯 Все пайплайны тестировались с **RealVisXL V5.0 Lightning**
- 💾 Для работы требуется **минимум 8-12 GB VRAM**
- 🔄 После установки плагинов **обязательно перезапускайте ComfyUI**
- 📸 В каждом пайплайне есть папка `examples` с примерами результатов и скриншотами графов

## 📄 Лицензия

Этот проект распространяется под лицензией MIT. Подробнее см. в файле [LICENSE](LICENSE).


⭐ **Если вам понравилась коллекция, поставьте звезду на GitHub!** ⭐