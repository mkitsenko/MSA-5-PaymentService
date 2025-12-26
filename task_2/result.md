| **Исходное состояние** | **Переходное состояние** | **Событие**                                         |
|:----------------------:|:------------------------:|:----------------------------------------------------|
|         START          |      ORDER_CREATED       | Создание заказа                                     |
|     ORDER_CREATED      |     PAYMENT_RESERVED     | Успешное резервирование средств                     |
|    PAYMENT_RESERVED    |   FRAUD_CHECK_STARTED    | Запуск анти-фрод проверки                           |
|  FRAUD_CHECK_STARTED   |  FRAUD_CHECK_SUCCEEDED   | Фрод проверка успешно пройдена                      |
|  FRAUD_CHECK_STARTED   |    FRAUD_CHECK_FAILED    | Фрод проверка не пройдена                           |
| FRAUD_CHECK_SUCCEEDED  |    PAYMENT_PROCESSED     | Проведение оплаты контрагенту                       |
|   PAYMENT_PROCESSED    |           END            | Завершение процесса                                 |
|   FRAUD_CHECK_FAILED   |    OPERATION_BLOCKED     | Блокировка операции                                 |
|   OPERATION_BLOCKED    |    PAYMENT_UNRESERVED    | Снятие резервирования денег клиента (возврат денег) |
|   OPERATION_BLOCKED    |        ALERT_SENT        | Отправка уведомления о неуспешной проверке          |
|       ALERT_SENT       |           END            | Завершение процесса                                 |
|   PAYMENT_UNRESERVED   |           END            | Завершение процесса                                 |
