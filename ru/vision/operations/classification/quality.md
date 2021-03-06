# Узнать качество изображения

_Классификация изображений сейчас находится на [стадии Preview](/docs/overview/concepts/launch-stages)._

Чтобы оценить качество изображения, воспользуйтесь возможностью [Классификация изображений](../../concepts/classification/index.md).

Для этого в методе [batchAnalyze](../../api-ref/Vision/batchAnalyze.md) в свойстве `type` укажите `Classification`, а в конфигурации укажите модель [quality](../../concepts/classification/supported-models.md#quality).

## Примеры {#examples}

[!INCLUDE [ai-before-beginning](../../../_includes/ai-before-beginning.md)]

### Применить модель для оценки качества {#basic}

1. Подготовьте файл изображения, соответствующий требованиям:

    [!INCLUDE [file-restrictions](../../../_includes/vision/file-restrictions.md)]

    > [!NOTE]
    >
    > Нужно изображение? [Скачайте пример](https://storage.yandexcloud.net/vision/face-detection-sample.jpg).
1. Кодируйте файл в формат Base64:

    [!INCLUDE [base64-encode-command](../../../_includes/vision/base64-encode-command.md)]
1. Создайте файл с телом запроса, например `body.json`. В свойстве `content` укажите изображение, [кодированное в Base64](../base64-encode.md):

    **body.json:**
    ```json
    {
        "folderId": "ajk55f3mblj12eghq2oe",
        "analyze_specs": [{
            "content": "iVBORw0KGgo...",
            "features": [{
                "type": "classification",
                "classificationConfig": {
                    "model": "quality"
                }
            }]
        }]
    }
    ```

1. [!INCLUDE [send-request](../../../_includes/vision/send-request.md)]

    В ответе будут содержаться признаки и вероятность соответствия этим признакам. По этим признакам вы можете модерировать изображение:

    [!INCLUDE [classification-quality-response](../../../_includes/vision/classification-quality-response.md)]

### Готовая функция для отправки запросов в bash {#oneliner}

1. [!INCLUDE [cli-install](../../../_includes/cli-install.md)]
1. Скопируйте в терминал функцию:

    ```bash
    vision_quality() {
        curl -H "Authorization: Bearer `yc iam create-token`" \
        "https://vision.api.cloud.yandex.net/vision/v1/batchAnalyze" \
        -d @<(cat << EOF
    {
        "folderId": "`yc config get folder-id`",
        "analyze_specs": [{
            "content": "`base64 -i $1`",
            "features": [{
                "type": "CLASSIFICATION",
                "classificationConfig": {
                    "model": "quality"
                }
            }]
        }]
    }
    EOF
    )
    }
    ```

    [!INCLUDE [oneline-function-hints](../../../_includes/vision/oneline-function-hints.md)]

1. Теперь вы можете вызывать эту функцию, передав путь к изображению в аргументах:

    ```bash
    vision_quality path/to/image.jpg
    ```