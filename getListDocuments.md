# Получение списка документов

Метод предназначен для формирования списка EDI и ЮЗДО-документов.

```GET /getListDocuments```

### Формат запроса

Запрос на получение списка документов следует отправлять с помощью метода GET.
```
/getListDocuments
? [id_type= <тип идентификатора>]
& [org_id= <идентификатор>]
& [document_type= <тип документа>]
& [sort= <тип сортировки>]
& [partner_org_id= <идентификатор>]
& [document_subtype= <подтип документа>]
& [limit= <количество документов>]
& [states= <статус документа>]
& [date_from= <дата>]
& [date_to= <дата>]
& [doc_read= <прочтение>]
& [read_date_from= <дата>]
& [read_date_to= <дата>]
```

### URL запроса 
```
https://dapi-preprod.ediweb.ru/edi/api/v1.1/getListDocuments?id_type=gln&org_id=2000000009994&document_type=WAYBILL_T1_ON_PTLSSOBTS &sort=Ascending&partner_org_id=2000000007705&document_subtype=Incoming&limit=10&date_from=2023-14-01&date_to=2023-14-03&doc_read=false
```

### Параметры запроса
| Параметр   | Описание | Пример значения | Тип данных |
|------------|----------|-----------------|------------|
|`id_type`*            |Тип идентификатора организации. Принимает значения: `gln` или `fns`          | gln                |string            |
|`org_id`*            |Идентификатор организации-инициатора запроса.	          | 2000000009994                | string           |
|`document_type`            |Тип документа          |WAYBILL_T1_ON_PTLSSOBTS                 |string            |
|`dete_from`*            |Дата документа с `yyyy-mm-dd`          |2023-10-01                 |string           |
|`date_to`*            |Дата документа по `yyyy-mm-dd`          |2023-10-03                 |string            |
|`sort`            |Ascending          |Порядок сортировки в выдаче                 |string            |
|`partner_org_id`            |Идентификатор организации-партнера          |2000000007705                 |string            |
|`document_subtype`            |Incoming          |Подтип выводимых сообщений                 |string            |
|limit            |Ограничение на количество выводимых документов, по умолчанию 100          |10                 |string            |
|states            |SENT          |Статус документа. Параметр может принимать несколько значений, в таком случае статусы указываются через запятую, без пробелов. Например, DRAFT,READ,SENT.                 |string          |
|`read_date_from`           |2023-12-01          |Дата прочтения документа с `yyyy-mm-dd`                 |data-time            |
|`read_date_to`           |2023-12-03         |Дата прочтения документа по `yyyy-mm-dd`                  |data-time            |
* Обязательный параметр

### Формат ответа

Если запрос обработан без ошибок, API возвращает код ответа `200`. Если запрос вызвал ошибку, возвращается соответствующий код ошибки и описание проблемы.

### Тело ответа
```
[[
 "WAYBILL_T1_ON_PTLSSOBTS",
 104021581
]]```

### Заголовки ответа
```
{
  "connection": "keep-alive",
  "content-length": "33",
  "content-type": "text/plain; charset=UTF-8",
  "date": "Fri, 14 Oct 2023 15:14:07 GMT",
  "request_uuid": "8e677a13-efd9-4f68-af4c-35d5ecc82362",
  "server": "nginx"
}
```