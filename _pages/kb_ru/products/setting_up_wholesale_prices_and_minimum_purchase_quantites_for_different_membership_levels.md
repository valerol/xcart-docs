---
lang: ru
layout: article_with_sidebar
updated_at: '2018-01-30 11:48 +0400'
identifier: ref_3BQKP6eU
title: Оптовые цены и минимальный объём покупки
order: 100
published: false
---
Используйте модуль **Wholesale**, чтобы установить оптовые цены и минимальное количество продуктов в заказе:

![1.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/1.jpg)

Один и тот же продукт предлагается по разным ценам в зависимости от группы, в которую входит покупатель, и от количества продукта в заказе.

Установите минимальное количество единиц одного продукта, которое покупатель должен купить. Если количество единиц продукта в заказе меньше минимального, оформление покупки невозможно.

## Настройка оптовых цен

1.  В интерфейсе администратора откройте страницу продукта, для которого хотите задать или изменить оптовые цены.
2.  Перейдите на вкладку **Оптовые цены**. 
   ![2.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/2.jpg)

3.  Создайте диапазон цен:
    1.  Нажмите **Новый диапазон**:
        ![3.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/3.jpg)

        Появится новая строка для редактирования:
        ![4.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/4.jpg)

    2. В поле **Диапазон количества** укажите количество продукта, с которого начинает действовать оптовая цена
    3.  В следующем поле укажите цену или долю цены в процентах, которая действует для указанного количества продукта:
    4.  Выберите группу пользователей, для которой действует специальная цена. 
        ![5.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/5.jpg)

    5. Нажмите **Сохранить**. В списке появиля новый диапазон цен:
       ![6.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/6.jpg)

Рассмотрим пример:

Установим цены на продукт для всех покупателей:

*   *   1-9 единиц- 3000 RUB
    *   10-99 единиц -2500 RUB
    *   100 и более единиц -1500 RUB

Чем больше количество продукта в заказе, тем ниже цена за единицу.

Для группы оптовых покупателей будут действовать специальные цены:

*   *   1-1000 единиц - 1000 RUB
    *   1001 и более единиц - 500 RUB

Как настроить такие цены:


*   *   Диапазон количества: от 1
        Цена: 3000 RUB
        Группа: Все покупатели
    *   Диапазон количества: от 10
        Цена: 2500 RUB
        Группа: Все покупатели
    *   Диапазон количества: от 100
        Цена: 1500 RUB
        Группа: Все покупатели
    *   Диапазон количества: от 1
        Цена: 1000 RUB
        Группа: Оптовые покупатели
    *   Диапазон количества: от 1000
        Цена: 500 RUB
        Группа: Оптовые покупатели

## Настройка минимального количества продукта для групп покупателей

Минимальное количество продукта для заказа настраивается в разделе **Контроль остатков** на странице продукта:

1.  Найдите продукт и перейдите на вкладку **Контроль остатков**
    ![7.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/7.jpg)

2. На вкладке **Контроль остатков** перейдите к разделу **Минимальное количество для покупки** и укажите минимальное количество продукта для каждой группы покупателей:
    ![8.jpg]({{site.baseurl}}/attachments/ref_3BQKP6eU/8.jpg)

3.  Нажмите **Сохранить**.

