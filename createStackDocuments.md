# Создание документов (пакетом)

Метод позволяет отправить в систему пакет состоящий из N-го количества документов. 

```POST /createStackDocuments```

### Формат запроса

Запрос запрос на создание пакета документов следует отправлять с помощью метода POST.

```
/createStackDocuments
? [id_type= <тип идентификатора>]
& [org_id= <идентификатор>]
```

### URL запроса 
```
https://dapi-preprod.ediweb.ru/edi/api/v1.1/createStackDocuments?id_type=gln&org_id=2000000009994
```

### Параметры запроса

| Параметр              | Описание                                                                                                                                                  | Пример значения                  | Тип данных  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|-------------|
| `id_type`*            | Тип идентификатора организации. Принимает значения: `gln` или `fns`                                                                                   | gln                            | string      |
| `org_id`*             | Идентификатор запроса организации-инициатора запроса                                                                                                    | 2000000009994                  | string      |
* Обязательный параметр

В теле запроса содержится zip-архив, внутри которого находится список файлов и опись пакета документов: 
* Если документ без подписи он передается в виде xml-документа.\
* Если документ подписан, то формируется архив. xml+подпись/подписи размещаются в корне архива, в случае с DSF еще вложение. 
* Формируется опись документов. Опись - xml-файл с метаинформацией к списку полученных документов. Имя файла Inventory.xml. XSD-схема с описанием - InventoryRequestAPI.xsd 

**Пример описи**
```
<?xml version="1.0" encoding="UTF-8"?>
<Documents>
    <Document>
        <Method>autosendDocument</Method>
        <DocumentType>LEGACY_ORDER</DocumentType>
        <SednerILN>2000000009994</SednerILN>
        <ReceiverILN>2000000007705</ReceiverILN>
        <FileName>ORDER_123.xml</FileName>
        <Number>123</Number>
        <DocFlowType>LEGACY</DocFlowType>
        <DocDate>2021-04-27</DocDate>
        <DocFlowID>5f1b9d30-a737-11eb-bcbc-0242ac130002</DocFlowID>
    </Document>
    <Document>
        <Method>createDocument</Method>
        <DocumentType>LEGACY_ORDER</DocumentType>
        <SednerILN>2000000009994</SednerILN>
        <ReceiverILN>2000000007705</ReceiverILN>
        <FileName>ORDER_456.xml</FileName>
        <Number>456</Number>
        <DocFlowType>LEGACY</DocFlowType>
        <DocDate>2021-04-27</DocDate>
        <DocFlowID>5f1b9fa6-a737-11eb-bcbc-0242ac130002</DocFlowID>
    </Document>
    <Document>
        <Method>createSignedTitulBySeller</Method>
        <DocumentType>EDI_FNS_UPD_P1</DocumentType>
        <VersionFormat>5.01-N</VersionFormat>
        <SednerILN>2000000009994</SednerILN>
        <ReceiverILN>2000000007705</ReceiverILN>
        <FileName>ON_NSCHFDOPPR_2LK5390D2B5A1E842FE9244528576B450AD_2IJAAC306AEBBF84A99841542A3AFD12494_20210504_91049022-b3c0-463c-abb2-450197793225.zip</FileName>
    </Document>
    <Totals>
        <TotalCount>2</TotalCount>
    </Totals>
</Documents>
```

### Формат ответа

Если запрос был обработан без ошибок, API отвечает кодом 200. В теле ответа возвращается перечень созданных документов с информацией о типах документов и их идентификаторы в системе.

Если запрос вызвал ошибку, возвращается подходящий код ответа, а тело ответа содержит описание ошибки.
### Тело ответа
```
[

{"documentType":"LEGACY_ORDER","fileName":"LEGACY_ORDER_63827739","docFlowID":"5f1b9d30-a737-11eb-bcbc-0242ac130002","doc_id":63827739},

{"documentType":"LEGACY_ORDER","fileName":"LEGACY_ORDER_63827740","docFlowID":"5f1b9fa6-a737-11eb-bcbc-0242ac130002","doc_id":63827740},

{"documentType":"EDI_FNS_UPD_P1","fileName":"ON_NSCHFDOPPR_2LK5390D2B5A1E842FE9244528576B450AD_2IJAAC306AEBBF84A99841542A3AFD12494_20210504_91049022-b3c0-463c-abb2-450197793225.zip","docFlowID":null,"error":"

{ \"fileName\": \"ON_NSCHFDOPPR_2LK5390D2B5A1E842FE9244528576B450AD_2IJAAC306AEBBF84A99841542A3AFD12494_20210504_91049022-b3c0-463c-abb2-450197793225.zip\",\n \"errorMessage\": \"controller.common.api.integration.error.common.api.execute.error\",\n \"additionalData\": \"message : The document is a duplicate docId = '42327695' and docType = 'EDI_FNS_UPD', docState = 'SENT'.\n\",\n \"typeError\": \"controller.common.api.integration.error.common.api.execute.error\"\n}
","doc_id":null}]
```

### Заголовки ответа
```

{
  "connection": "keep-alive",
  "content-disposition": "attachment; filename=StackDocuments_RESPONSE_26052021083533.zip",
  "content-length": "2770",
  "content-type": "text/plain; charset=UTF-8",
  "date": "Wed, 26 May 2021 08:35:45 GMT",
  "file_name": "U3RhY2tEb2N1bWVudHNfUkVTUE9OU0VfMjYwNTIwMjEwODM1MzMuemlw",
  "request_uuid": "54107d0c-2fa9-4b11-8658-c0cd53418c2b",
  "server": "nginx"
}
```
