Bootstrap 4 date/time picker widget for Yii2
============================================

Credits
-------
Jonathan Peterson (@Eonasdan) for [Bootstrap 4 Date/Time Picker](https://github.com/Eonasdan/bootstrap-datetimepicker).

Antonio Ramirez (@tonydspaniard) for inspiration by [Bootstrap DatePicker Widget for Yii2](https://github.com/2amigos/yii2-date-picker-widget) and code examples.

Installation
------------
The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

```shell
composer require buibr/yii2-datepicker-bs4
```

Usage
-----
Please refer to the [Datepicker documentation](http://eonasdan.github.io/bootstrap-datetimepicker/) web page for options and examples of using Eonasdan's Datepicker widget.

To use widget as date/time picker, set appropriate format, e.g. 'L LT' (as in examples below). See [momentjs' docs](http://momentjs.com/docs/#/displaying/format/) for valid formats.

**With a model**

```php
use buibr\datepicker\DatePicker;

print DatePicker::widget([
    'model' => $model,
    'attribute' => 'attrName',
    'language' => 'ru',
    'size' => 'lg',
    'readonly' => true,
    'placeholder' => 'Choose date',
    'clientOptions' => [
        'format' => 'L',
        'minDate' => '2015-08-10',
        'maxDate' => '2015-09-10',
    ],
    'clientEvents' => [
        'dp.show' => new \yii\web\JsExpression("function () { console.log('It works!'); }"),
    ],
])
```

```php

$config = [
    'addon' => false,
    'size' => 'sm',
    'clientOptions' => [
        'format' => 'L LT',
        'stepping' => 30,
    ],
];

print $form->field($model, 'attrName')->widget(DatePicker::className(), $config);
```

**Without a model**

```php
use buibr\datepicker\DatePicker;

print DatePicker::widget([
    'name' => 'datepickerTest',
    'value' => '09/13/2015',
    'clientOptions' => [
        'format' => 'L',
    ],
    'dropdownItems' => [
        ['label' => 'Yesterday', 'url' => '#', 'value' => \Yii::$app->formatter->asDate('-1 day')],
        ['label' => 'Tomorrow', 'url' => '#', 'value' => \Yii::$app->formatter->asDate('+1 day')],
        ['label' => 'Some value', 'url' => '#', 'value' => 'Special value'],
    ],
])
```
