
Лабораторна робота 6 (Методи машинного навчання). Відтворення демо за науковою статтею
1.	Стаття
DETR: End-to-End Object Detection with Transformers (2020)
Автори: Nicolas Carion, Francisco Massa, Gabriel Synnaeve, Nicolas Usunier, Alexander Kirillov, Sergey Zagoruyko
Посилання на статтю: https://arxiv.org/abs/2005.12872
2.	Оригінальний код на GitHub
https://github.com/facebookresearch/detr
3.	Мета цього репозиторію
У репозиторії наведено відтворюваний запуск standalone демо з офіційного GitHub DETR та продемонстровано одне практичне покращення інференсу в коді: мульти-масштабну test-time augmentation (TTA) з клас-орієнтованою non-maximum suppression (NMS). Мета роботи полягає у тому, щоб показати коректний запуск демо та вплив інференсної постобробки на результат детекції.
4.	Виконані дії
a) Запущено standalone демо в Google Colab із pretrained моделлю DETR.
b) Зафіксовано результати роботи демо.
c) Додано multi-scale TTA (використано декілька масштабів Resize під час інференсу) та застосовано NMS по класах для зменшення дублюючих рамок.
5.	Як запустити: відкрити Google Colab: https://colab.research.google.com/drive/1YJJcln0ONLTER-X8lSivaIpMtn4_BPBT?authuser=2#scrollTo=kqe_0nc5dyAq
Відкрити Colab-ноутбук та виконати всі комірки зверху вниз.
Або Python-скрипт
Встановити залежності:
pip install torch torchvision matplotlib pillow requests
Запустити:
python detr_demo.py
6.	Результати (приклад для COCO зображення 000000039769.jpg)
Базовий інференс (один масштаб 800): 5 детекцій
TTA інференс (масштаби 800, 1000, 1200): 6 детекцій
Максимальна впевненість для класу couch не змінилася, тоді як додаткова детекція з’явилася для дрібного об’єкта (remote), що демонструє, що multi-scale інференс сильніше впливає на малі або складні об’єкти.
7.	Структура репозиторію
detr_demo.py містить демо-код та додану логіку TTA і NMS
images містить скріншоти результатів демо (base та TTA) і вивід у консолі
