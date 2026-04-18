Пратика пентестинга LLM-агентов по следующей цепочке атак `tool enumeration`->`tool explotation`
1. Установите уязвимый LLM агент https://github.com/AI-Threat-Team/vulnerable-llm-agent в соответствие с  инструкациями в README.md
2. Запустите LLM бэкенд  в OpenAI API поддерживаемом формате
- ollama: https://docs.ollama.com/api/openai-compatibility
- llama.cpp: https://github.com/ggml-org/llama.cpp/tree/master/tools/server

3.Запустите основной терминал агента и терминал отладки
```
# Терминал 1 — Пользовательский интерфейс
uv run python main.py                   # Английский (по умолчанию)
uv run python main.py --language ru     # Русский
uv run python main.py -l ru             # Короткая форма

# Терминал 2 — Отладочный просмотрщик (полная трассировка)
uv run python debug.py
```
