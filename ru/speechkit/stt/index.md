# Распознавание речи

_Распознавание речи (speech-to-text — stt)_ — это процесс преобразования речи в текст.

Сервис позволяет распознавать речь на языках:

* русский;
* английский;
* турецкий.

## Способы распознавания {#stt-ways}

Есть три способа распознавания:

1. [Распознавание коротких аудиофайлов](request.md).
1. [Распознавание длинных аудиофайлов](transcribation.md). _Распознавание длинных аудиофайлов находится на [стадии Preview](../../overview/concepts/launch-stages)._
1. [Потоковое распознавание](streaming.md).

## Процесс распознавания {#process}

Распознавание аудио происходит в три этапа:

1. Выделяются слова. Обычно существует несколько гипотез распознанного слова.
1. Гипотезы проверяются с помощью языковой модели. Модель проверяет, насколько согласуется новое слово со словами, распознанными ранее.
1. Обрабатывается распознанный текст — числительные преобразуются в цифры, расставляются некоторые знаки препинания (например, дефисы) и т. д. Этот преобразованный текст и является финальным результатом распознавания, который отправляется в теле ответа.

## Точность распознавания {#speed_and_accuracy}

Чтобы повысить точность распознавания, уточните языковую модель, которую должен использовать сервис. Модель должна соответствовать тематике речи.

Еще на точность распознавания влияют:
* качество исходного звука;
* качество кодирования аудио;
* разборчивость и темп речи;
* сложность фраз и их длина.

#### См. также

* [[!TITLE]](formats.md)
* [[!TITLE]](models.md)
* [[!TITLE]](request.md)
* [[!TITLE]](streaming.md)
* [[!TITLE]](transcribation.md)
* [Речевые технологии Яндекса (пост на Хабрахабре)](https://habrahabr.ru/company/yandex/blog/243813/)
* [Под капотом у Yandex.SpeechKit (пост на Хабрахабре)](https://habrahabr.ru/company/yandex/blog/198556/)
