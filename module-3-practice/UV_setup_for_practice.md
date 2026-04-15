# Настройка окружения для практической работы через uv

Ниже — простой вариант setup под Ubuntu/Linux, чтобы:

1. установить **uv**;
2. поднять Python-окружение для ноутбука;
3. установить **Jupyter / ipykernel** для `ipynb`;
4. установить **Heretic**;
5. установить **Ollama**.

---

## 0. Загрузка репозитория с практикой

```bash
git clone https://github.com/AI-Threat-Team/ai-system-security.git
```

## 0.1. Установка Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```


## 1. Установка uv

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

После установки перезапусти терминал или выполни:

```bash
source ~/.bashrc
```

---

## 2. Создание рабочей папки и виртуального окружения

```bash
Заходи в нужную практику и устанавливай пакеты

uv python install 3.11
uv venv --python 3.11
source .venv/bin/activate
```

---

## 3. Установка Jupyter и библиотек для ноутбука

### 3.1 Базовые пакеты для `.ipynb`

```bash
export UV_HTTP_TIMEOUT=120
uv pip install jupyterlab ipykernel notebook requests pandas matplotlib
uv pip install torch --index-url https://download.pytorch.org/whl/cu128

```

### 3.2 Устанавливаем Heretic

```bash
git clone https://github.com/p-e-w/heretic.git
cd heretic
uv pip install -e .

Вносим правки в код!

1. Расширяем список слов, на которых мы считаем, что модель нам отказала в ответе. Правим файл config.py:

```
refusal_markers = [
    "i cannot",
    "i can't",
    "i can not",
    "i won't",
    "i will not",
    "i'm not able",
    "i am not able",
    "i'm unable",
    "i am unable",
    "i'm sorry",
    "i am sorry",
    "i apologize",
    "i must decline",
    "i have to decline",
    "i must refuse",
    "i'd rather not",
    "i would rather not",
    "i'm not comfortable",
    "i am not comfortable",
    "i cannot fulfill",
    "i cannot help",
    "i cannot assist",
    "i cannot provide",
    "i cannot write",
    "i cannot create",
    "i cannot generate",
    "cannot comply",
    "not something i can",
    "against my guidelines",
    "against my programming",
    "goes against",
]
```

2. Выключаем мышление мягким способом токеном /no_think в системном промте в файле config.py

3. Выключаем мышление (enable_thinking) в chat_template в файле model.py

### 3.3 Регистрация ядра Jupyter

```bash
python -m ipykernel install --user --name module-2-4 --display-name "Python (module-2-4)"
```

### 3.4 Запуск Jupyter

```bash
jupyter notebook
```

После запуска открой ноутбук и выбери kernel.

---
