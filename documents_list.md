# Типы документов

Этот список включает в себя типы документов, которые используются на платформе Dropcat. Он охватывает различные виды заказов, поручений, электронных транспортных накладных (ЭТРН), путевых листов и нотификаций, которые могут быть необходимы в процессе транспортировки и логистики.
Каждый документ имеет свою специфическую роль и используется для выполнения определённых операций на платформе. 

## Заказ и поручение
- `FORWARDING_ORDER` — Поручение экспедитору
- `TRANSPORT_IFTMBP` — Предварительный запрос на автотранспорт
- `TRANSPORT_IFTMBC` — Ответ на предварительный запрос на автотранспорт

## Электронная транспортная накладная (ЭТРН)
- `ETRN_FNS_GO` — Титул 1 Грузоотправитель
- `ETRN_FNS_TK_LOAD` — Титул 2 Транспортная компания (погрузка)
- `ETRN_FNS_GP` — Титул 3 Грузополучатель
- `ETRN_FNS_TK_UNLOAD` — Титул 4 Транспортная компания (разгрузка)
- `ETRN_FNS_TK_CHANGE_FINANCE` — Титул 5 Перевозчик (изменение финансовых сведений)
- `ETRN_FNS_GO_CHANGE_FINANCE*` — Титул 6 Грузоотправитель (подтверждение изменения финансовых сведений)
- `ETRN_FNS_TK_READDRESS` — Титул 7 Переадресовка
- `ETRN_FNS_TK_CORRECT` — Титул 8 Замена водителя или транспортного средства
- `ETRN_FNS_DP_UVUTOCH` — Уведомление об уточнении
- `ETRN_FNS_UVPERADR` — Уведомление о переадресовке

## Путевой лист
- `WAYBILL_T1_ON_PTLSSOBTS` — Обстоятельства и особенности рейса (Титул 1)
- `WAYBILL_T2_ON_PTLSPRMO` — Результат предсменного, предрейсового медицинского осмотра (Титул 2)
- `WAYBILL_T3_ON_PTLSVIPTS` — Выпуск транспортного средства на линию (Титул 3)
- `WAYBILL_T4_ON_PTLSODVZD` — Показания одометра (выезд/прием транспортного средства) (Титул 4)
- `WAYBILL_T5_ON_PTLSODPARK` — Показания одометра (заезд/сдача транспортного средства) (Титул 5)
- `WAYBILL_T6_ON_PTLSPOSMO` — Результат послесменного, послерейсового медицинского осмотра (Титул 6)

## Нотификация
- `EDI_CONTRL` — Нотификация
