---
lang: ru
layout: article_with_sidebar
updated_at: '2018-02-05 09:25 +0400'
identifier: ref_3dUIvN13
title: Статусы платёжных операций в X-Cart
order: 40
published: true
---
Каждому заказу в магазине присваивается статус платёжной операции для отслеживания стадии обработки заказа. 

{% note info %}
Платёжная операция - это не банковская операция в общем смысле. Платёжная операция создаётся, когда клиент начинает оплату заказа онлайн или офлайн способом. Разница заключается в заказе. При офлайн оплате заказ создаётся, когда покупатель нажимает кнопку **Разместить заказ**, при этом платёжная операция автоматически получает статус **Ожидает модерации**. При успешной онлайн оплате в магазине создаётся заказ со статусом платёжной операции **Успешная**. Если оплата не прошла, заказ не создаётся, но регистрируется платёжная операция в статусе **Не прошла**. В момент неудачного платежа корзина покупателя не блокируется, и покупатель может добавить или удалить товары. Чтобы корзина покупателя блокировалась, необходим модуль {% link "Not Finished Orders" ref_6K7lCFaI %}.
{% endnote %}

Информация о платёжных операциях доступна администратору магазина на странице **Заказы / Платёжные операции**.
![1.jpg]({{site.baseurl}}/attachments/ref_3dUIvN13/1.jpg)

На этой странице возможен поиск заказов по статусу платёжной операции.

X-Cart использует следующие статусы платёжных операций:

{:.ui.compact.celled.small.padded.table}
| В процессе | Покупатель приступил к оплате - нажал кнопку **Разместить заказ** и начал вводить данные кредитной карты.|
| Успешна | Заказ успешно оплачен и денежные средства переведены. |
| Ожидает модерации | Оплата заказа на рассмотрении. Статус по умолчанию присваивается заказам, для которых выбрана офлайн оплата. |
| Не прошла | По техническим причинам или из-за временных неполадок не произошла авторизация платежа или списание средств с карты.|
| Отменена | Заказ отменён продавцом. Оплата полностью возвращена покупателю. |
| Пустая | Оплата кредитной картой отменена продавцом после авторизации, но до завершения обработки платежа. Пустая транзакция не появляется в выписке по карте клиента, но может появиться в списке ожидающих обработки операций в банковском личном кабинете. |

{% note info %}
У незавершённых транзакций появляется иконка **Подробнее**, которая объясняет причину сбоя оплаты.
{% endnote %}
