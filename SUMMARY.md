---
title: Содержание
order: 0.1
---

[html]

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flow CRM — Справка</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif; background: #F5F7FF; color: #2C2C2A; line-height: 1.5; }
  .page { max-width: 860px; margin: 0 auto; padding: 2rem 1.25rem 3rem; }

  /* HERO */
  .hero { background: #EEF2FB; border-radius: 16px; padding: 2rem; margin-bottom: 1.25rem; border: 0.5px solid #D3D8EE; }
  .hero-logo { display: flex; align-items: center; gap: 8px; margin-bottom: 1rem; }
  .logo-mark { width: 28px; height: 28px; border-radius: 7px; background: #3DCFCA; display: flex; align-items: center; justify-content: center; }
  .logo-name { font-size: 15px; font-weight: 500; color: #2C2C2A; }
  .hero-badge { display: inline-flex; align-items: center; background: #E1F5EE; border: 0.5px solid #5DCAA5; border-radius: 20px; padding: 3px 10px; margin-bottom: .85rem; }
  .hero-badge span { font-size: 11px; color: #085041; }
  .hero h1 { font-size: 22px; font-weight: 500; color: #1a1a1a; line-height: 1.35; margin-bottom: .55rem; }
  .hero p { font-size: 13px; color: #5F5E5A; line-height: 1.65; max-width: 520px; margin-bottom: 1.25rem; }
  .hero-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 1rem; }
  .stat { background: #fff; border-radius: 10px; padding: .75rem; text-align: center; border: 0.5px solid #D3D8EE; }
  .stat-num { font-size: 19px; font-weight: 500; color: #3DCFCA; }
  .stat-label { font-size: 11px; color: #888780; margin-top: 2px; line-height: 1.35; }

  /* BUTTONS */
  .cta-row { display: flex; gap: 8px; margin-bottom: 1.25rem; flex-wrap: wrap; }
  .btn-p { background: #3DCFCA; color: #fff; border: none; border-radius: 8px; padding: .55rem 1.1rem; font-size: 13px; font-weight: 500; cursor: pointer; text-decoration: none; display: inline-block; }
  .btn-s { background: #fff; color: #2C2C2A; border: 0.5px solid #B4B2A9; border-radius: 8px; padding: .55rem 1.1rem; font-size: 13px; cursor: pointer; text-decoration: none; display: inline-block; }
  .btn-p:hover { opacity: .9; } .btn-s:hover { background: #F1EFE8; }

  /* FREE BANNER */
  .free-banner { background: #EEEDFE; border-radius: 12px; padding: 1rem 1.1rem; display: flex; align-items: center; justify-content: space-between; gap: 1rem; margin-bottom: 1.25rem; border: 0.5px solid #AFA9EC; }
  .free-banner p:first-child { font-size: 13px; font-weight: 500; color: #3C3489; }
  .free-banner p:last-child { font-size: 11px; color: #534AB7; margin-top: 2px; }
  .free-btn { background: #534AB7; color: #fff; border: none; border-radius: 8px; padding: .5rem 1rem; font-size: 12px; font-weight: 500; cursor: pointer; white-space: nowrap; flex-shrink: 0; text-decoration: none; display: inline-block; }
  .free-btn:hover { opacity: .9; }

  /* SECTION LABEL */
  .sec-label { font-size: 11px; font-weight: 500; color: #888780; text-transform: uppercase; letter-spacing: .07em; margin-bottom: .65rem; }

  /* WHO GRID */
  .who-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 8px; margin-bottom: 1.25rem; }
  .who-card { background: #fff; border: 0.5px solid #D3D1C7; border-radius: 12px; padding: .85rem; cursor: pointer; transition: border-color .15s; text-decoration: none; display: block; }
  .who-card:hover { border-color: #3DCFCA; }
  .who-dot { width: 6px; height: 6px; border-radius: 50%; background: #3DCFCA; margin-bottom: .5rem; }
  .who-card h4 { font-size: 13px; font-weight: 500; color: #2C2C2A; margin-bottom: .25rem; }
  .who-card p { font-size: 11px; color: #5F5E5A; line-height: 1.5; }

  /* FEAT GRID */
  .feat-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 1.25rem; }
  .feat { background: #fff; border: 0.5px solid #D3D1C7; border-radius: 12px; padding: .85rem; cursor: pointer; transition: border-color .15s; text-decoration: none; display: block; }
  .feat:hover { border-color: #3DCFCA; }
  .feat-icon { width: 32px; height: 32px; border-radius: 8px; display: flex; align-items: center; justify-content: center; margin-bottom: .6rem; }
  .feat h4 { font-size: 12px; font-weight: 500; color: #2C2C2A; margin-bottom: .2rem; line-height: 1.35; }
  .feat p { font-size: 11px; color: #5F5E5A; line-height: 1.45; }

  /* METRICS */
  .metrics { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 1.25rem; }
  .metric { background: #F1EFE8; border-radius: 10px; padding: .85rem; text-align: center; }
  .metric-big { font-size: 20px; font-weight: 500; color: #2C2C2A; }
  .metric-label { font-size: 11px; color: #5F5E5A; margin-top: 3px; line-height: 1.4; }
  .metric-sub { font-size: 10px; color: #3DCFCA; margin-top: 4px; font-weight: 500; }

  /* FLOW STEPS */
  .flow-wrap { background: #F1EFE8; border-radius: 12px; padding: 1.1rem; margin-bottom: 1.25rem; }
  .flow-steps { display: grid; grid-template-columns: repeat(6, 1fr); gap: 4px; }
  .fstep { text-align: center; position: relative; padding: 0 .15rem; cursor: pointer; }
  .fstep:not(:last-child)::after { content: '→'; position: absolute; right: -7px; top: 12px; color: #3DCFCA; font-size: 13px; font-weight: 500; }
  .fstep-n { width: 26px; height: 26px; border-radius: 50%; background: #3DCFCA; color: #fff; font-size: 11px; font-weight: 500; display: flex; align-items: center; justify-content: center; margin: 0 auto .4rem; }
  .fstep-l { font-size: 10px; font-weight: 500; color: #2C2C2A; line-height: 1.3; }
  .fstep-s { font-size: 9px; color: #888780; margin-top: .15rem; line-height: 1.3; }
  .fstep:hover .fstep-n { opacity: .8; }

  /* LINKS GRID */
  .links-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 7px; margin-bottom: 1.25rem; }
  .lnk { display: flex; align-items: center; gap: 9px; padding: .65rem .9rem; background: #fff; border: 0.5px solid #D3D1C7; border-radius: 8px; cursor: pointer; transition: border-color .15s; text-decoration: none; }
  .lnk:hover { border-color: #3DCFCA; }
  .lnk-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
  .lnk span { font-size: 12px; color: #2C2C2A; }

  /* QUOTE */
  .quote { border-left: 3px solid #3DCFCA; padding: .85rem 1rem; margin-bottom: 1.25rem; background: #F1EFE8; border-radius: 0 8px 8px 0; }
  .quote p { font-size: 12px; color: #5F5E5A; line-height: 1.6; font-style: italic; }
  .quote-author { font-size: 11px; color: #3DCFCA; margin-top: .5rem; font-weight: 500; }

  @media (max-width: 560px) {
    .feat-grid { grid-template-columns: repeat(2, 1fr); }
    .flow-steps { grid-template-columns: repeat(3, 1fr); }
    .fstep:nth-child(3)::after { display: none; }
    .hero-stats { grid-template-columns: 1fr 1fr; }
    .metrics { grid-template-columns: 1fr 1fr; }
  }
  @media (max-width: 400px) {
    .who-grid, .links-grid { grid-template-columns: 1fr; }
    .feat-grid { grid-template-columns: 1fr; }
    .flow-steps { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>
<div class="page">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-logo">
      <div class="logo-mark">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M8 2C4.7 2 2 4.7 2 8s2.7 6 6 6 6-2.7 6-6-2.7-6-6-6zm0 2.5c.8 0 1.5.7 1.5 1.5S8.8 7.5 8 7.5 6.5 6.8 6.5 6 7.2 4.5 8 4.5zm0 7.5c-1.7 0-3.1-.8-4-2.1.1-1.3 2.7-2 4-2s3.9.7 4 2c-.9 1.3-2.3 2.1-4 2.1z" fill="#fff"/></svg>
      </div>
      <span class="logo-name">Flow CRM — справка</span>
    </div>
    <h1>Заявки, документы, зачисление — в одной системе</h1>
    <p>Flow помогает образовательным организациям вести слушателей от подачи заявки до выдачи документа. Онлайн-заявки, генерация договоров и приказов, интеграция с LMS Odin.</p>
</body>
</html>

[/html]

-  [Быстрый старт](./Start)

-  [Организация](./Organization/_index)

   -  [Создание организации](./Organization/sozdanie-organizacii)

   -  [Подписанты](./Organization/podpisanty)

   -  [Токен организации](./Organization/Token/_index)

      -  [Форма сбора заявок на сайте организации](./Organization/Token/forma-sbora-zayavok-na-saite-organizacii)

      -  [Форма сбора заявок на примере Tilda](./Organization/Token/forma-sbora-zayavok-na-primere-tilda/_index)

   -  [Шаблоны документов](./Organization/Shablony/_index)

      -  [Создание собственных шаблонов](./Organization/Shablony/sozdanie-sobstvennykh-shablonov)

      -  [Префикс организации для генерируемых документов](./Organization/Shablony/prefiks-organizacii-dlya-generiruemykh-dokumentov/_index)

      -  [Ключевые слова](./Organization/Shablony/klyuchevye-slova)

   -  [Дополнительные документы и поля ввода данных](./Organization/dopolnitelnye-dokumenty-i-polya-vvoda-dannykh/_index)

   -  [Как войти с Яндекс ID](https://www.flow-crm.study/helpcrm/Organization/kak-voiti-s-yandeks.klyuchom)

-  [Сотрудники](./sotrudniki)

## Обучение

-  [Программа](./obuchenie/Programma/_index)

   -  [Стоимость программы](./obuchenie/Programma/stoimost-programmy)

   -  [Дополнительные поля и файлы](./Organization/dopolnitelnye-dokumenty-i-polya-vvoda-dannykh/_index)

   -  [Поток](./obuchenie/Potok/_index)

      -  [Экспорт для ФИС ФРДО](./obuchenie/Potok/eksport-dlya-fis-frdo)

   -  [Выгрузка для ЦЗН](./obuchenie/Programma/vygruzka-dlya-czn)

-  [Приказы](./obuchenie/prikaz/_index)

   -  [Добавление приказов вручную](./obuchenie/prikaz/dobavlenie-prikazov-vruchnuyu)

   -  [Автоматический выпуск](./obuchenie/prikaz/avtomaticheskii-vypusk)

## Слушатели

-  [Заявки](./slushateli/zayavki/_index)

   -  [Способы создания заявок](./slushateli/zayavki/sposoby-sozdaniya-zayavok/_index)

   -  [Этапы работы с заявкой](./slushateli/zayavki/etapy-raboty-s-zayavkoi)

   -  [Генерация договоров со слушателями](./slushateli/zayavki/generaciya-dogovorov-so-slushatelyami)

   -  [Завершение обучения](./slushateli/zayavki/zavershenie-obucheniya)

   -  [Слушатели.Краткое руководство](https://www.flow-crm.study/helpcrmstud)

-  [Импорт](./slushateli/import/_index)

## Роли

-  [Назначение ролей](./chasto-zadavaemye-voprosy/kakie-roli-dostupny-vo-flow-crm)

## ИНСТРУКЦИИ

-  [Интеграция с LMS Odin](./integracii/integraciya-s-lms-odin)

-  [Как происходит онлайн-оплата?](./instrukcii/kak-proiskhodit-onlain-oplata)

-  [Как поставить отметку об оплате?](./instrukcii/kak-postavit-otmetku-ob-oplate)

-  [Как работать с тегами в заявках?](./instrukcii/kak-rabotat-s-tegami-v-zayavkakh/_index)

---

-  [Как работать с дополнительными полями?](./instrukcii/kak-rabotat-s-dopolnitelnymi-polyami/_index)

-  [Как работать с внешними источниками?](./instrukcii/kak-rabotat-s-vneshnimi-istochniki)

-  [Как сделать рассылку?](./instrukcii/kak-sdelat-rassylku)

## Часто задаваемые вопросы

-  [Как отклонить заявку?](./chasto-zadavaemye-voprosy/kak-otklonit-zayavku)

-  [Как меняются этапы в заявке и шаги в ЛК слушателя? (подробно)](./chasto-zadavaemye-voprosy/kak-menyayutsya-etapy-v-zayavke-i-shagi-v-lk-slushatelya-podrobno)