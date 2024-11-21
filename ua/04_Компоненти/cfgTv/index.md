
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>CfgTv: системні налаштування зі списку TV параметрів із вказаного документа</h3>
Створює системні налаштування зі списку TV параметрів із вказаного документа.
<p>Багато хто любить і активно використовує налаштування сайту через <code>[[getField? name=`tv_name` ...]]]</code>, створюючи ресурс, де всі ці налаштування зберігаються в TV. Але є проблема: кожне таке налаштування = 1 запит, а це означає більше часу на генерацію + незручно.</p>
<p>А що, якщо робити так само, але виклик на сторінці буде <code>[(cfg_footer_phone)]</code>, <code>[(cfg_icq)]</code> і так далі? Зручно, правда?</p>
<p>Рішення: CfgTv</p>
<p>Подія: <code>OnBeforeDocFormSave</code></p>

```php
/**
 * CfgTv 0.1
 * Save TV as system setting from some resourse 
 * 
 *
 * @category    plugin
 * @version     1.0.0b
 * @author      Bumkaka
 * @internal    @properties &ids=ID ресурсів налаштувань;text;347 &prefix=Префікс;text;cfg_
 * @internal    @events OnBeforeDocFormSave
 * @internal    @modx_category Manager and Admin
 */

<?php

switch (evo()->event->name) {
  case 'OnBeforeDocFormSave':
    $list_id = explode(',', $ids);
    if (!in_array($_POST['id'], $list_id)) {
      return;
    }

    $SQL = "SELECT * FROM " . evo()->getFullTableName('site_tmplvars') . ";";
    $result = evo()->db->query($SQL);

    while ($row = evo()->db->getRow($result)) {
      $TVNAME[$row['id']] = $row['name'];
    }

    foreach ($_POST as $key => $value) {
      if (substr($key, 0, 2) != 'tv') {
        continue;
      }
      $id = substr($key, 2, strlen($key));
      $name = $prefix . $TVNAME[$id];
      $settings[$name] = $value;
      $SQL = "SELECT * FROM " . evo()->getFullTableName('system_settings') . " WHERE `setting_name`='" . $name . "'";
      $count = evo()->db->getRow(evo()->db->query($SQL));
      if (!empty($count['setting_name'])) {
        $SQL = "UPDATE " . evo()->getFullTableName(
            'system_settings'
          ) . " SET `setting_value`='" . $value . "' WHERE `setting_name`='" . $name . "'";
        evo()->db->query($SQL);
      } else {
        $SQL = "INSERT into " . evo()->getFullTableName(
            'system_settings'
          ) . " SET `setting_name`='" . $name . "',`setting_value`='" . $value . "'";
        evo()->db->query($SQL);
      }
    }
    break;
}
```