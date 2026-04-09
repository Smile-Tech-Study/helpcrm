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

[html]

<p><style>
.sd*{box-sizing:border-box}
.sd{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;font-size:14px;color:#2C2C2A;padding:8px 0}
.sd-start{background:#E6F1FB;border-radius:12px;padding:20px 24px;margin-bottom:28px;border:0.5px solid #85B7EB}
.sd-start-label{font-size:11px;text-transform:uppercase;letter-spacing:.06em;font-weight:500;color:#185FA5;margin-bottom:10px}
.sd-start-title{font-size:18px;font-weight:500;color:#0C447C;margin-bottom:8px}
.sd-start-desc{font-size:13px;color:#185FA5;line-height:1.5;margin-bottom:16px}
.sd-start-links{display:flex;flex-wrap:wrap;gap:6px}
.sd-start-link{font-size:12px;padding:6px 14px;border-radius:20px;background:#fff;border:0.5px solid #85B7EB;color:#185FA5;text-decoration:none;font-weight:500;transition:all .15s}
.sd-start-link:hover{background:#B5D4F4}
.sd-map-title{font-size:11px;text-transform:uppercase;letter-spacing:.06em;font-weight:500;color:#888780;margin-bottom:14px}
.sd-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
@media(max-width:600px){.sd-grid{grid-template-columns:1fr}}
@media(min-width:601px) and (max-width:860px){.sd-grid{grid-template-columns:repeat(2,1fr)}}
.sd-card{border:0.5px solid #D3D1C7;border-radius:12px;background:#fff;padding:16px}
.sd-card-head{display:flex;align-items:center;gap:10px;margin-bottom:10px}
.sd-card-icon{width:30px;height:30px;border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.sd-card-title{font-size:14px;font-weight:500;color:#2C2C2A;text-decoration:none}
.sd-card-title:hover{color:#185FA5}
.sd-links{display:flex;flex-direction:column;gap:2px}
.sd-link{font-size:12px;color:#5F5E5A;text-decoration:none;padding:3px 0;line-height:1.4}
.sd-link:hover{color:#185FA5}
.sd-link-sub{padding-left:10px;color:#888780}
.sd-link-sub:hover{color:#185FA5}
</style>

<div class="sd">

  <div class="sd-start">
    <div class="sd-start-label">Новый пользователь</div>
    <div class="sd-start-title">С чего начать работу во Flow</div>
    <div class="sd-start-links">
      <a class="sd-start-link" href="https://www.flow-crm.study/helpcrm/Start" target="_blank">Быстрый старт →</a>
      <a class="sd-start-link" href="https://www.flow-crm.study/helpcrm/Organization/sozdanie-organizacii" target="_blank">Создание организации</a>
      <a class="sd-start-link" href="https://www.flow-crm.study/helpcrm/Organization/Shablony" target="_blank">Шаблоны документов</a>
      <a class="sd-start-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma" target="_blank">Создать программу</a>
      <a class="sd-start-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Potok" target="_blank">Создать поток</a>
    </div>
  </div>

  <div class="sd-map-title">Все разделы справки</div>
  <div class="sd-grid">

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#E6F1FB">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/Organization" target="_blank">Организация</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/sozdanie-organizacii" target="_blank">Создание организации</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/podpisanty" target="_blank">Подписанты</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/Token" target="_blank">Токен организации</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/Organization/Token/forma-sbora-zayavok-na-saite-organizacii" target="_blank">Форма сбора заявок</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/Shablony" target="_blank">Шаблоны документов</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/Organization/Shablony/sozdanie-sobstvennykh-shablonov" target="_blank">Создание шаблонов</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/Organization/Shablony/klyuchevye-slova" target="_blank">Ключевые слова</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/dopolnitelnye-dokumenty-i-polya-vvoda-dannykh" target="_blank">Доп. документы и поля</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/Organization/vneshnie-istochniki" target="_blank">Внешние источники</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/sotrudniki" target="_blank">Сотрудники</a>
      </div>
    </div>

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#E6F1FB">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/obuchenie" target="_blank">Обучение</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma" target="_blank">Программа</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma/stoimost-programmy" target="_blank">Стоимость программы</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma/tipy-programm-i-urovni-obrazovaniya" target="_blank">Типы программ</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Potok" target="_blank">Поток</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/obuchenie/Potok/eksport-dlya-fis-frdo" target="_blank">Экспорт для ФИС ФРДО</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz" target="_blank">Приказы</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz/dobavlenie-prikazov-vruchnuyu" target="_blank">Ручной выпуск</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz/avtomaticheskii-vypusk" target="_blank">Автоматический выпуск</a>
      </div>
    </div>

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#E6F1FB">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/slushateli" target="_blank">Слушатели</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki" target="_blank">Заявки</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/sposoby-sozdaniya-zayavok" target="_blank">Способы создания заявок</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/etapy-raboty-s-zayavkoi" target="_blank">Этапы работы с заявкой</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/generaciya-dogovorov-so-slushatelyami" target="_blank">Генерация договоров</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/zavershenie-obucheniya" target="_blank">Завершение обучения</a>
        <a class="sd-link sd-link-sub" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/nabor-dokumentov-sobiraemyy-v-sisteme" target="_blank">Документы в заявке</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/slushateli/import" target="_blank">Импорт</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrmstud" target="_blank">Справка для слушателей</a>
      </div>
    </div>

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#E1F5EE">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#085041" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/integracii" target="_blank">Интеграции</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/integracii/integraciya-s-lms-odin" target="_blank">Интеграция с LMS Odin</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/integracii/aktivnye-mery-po-sodeystviyu-zanyatosti" target="_blank">Активные меры по содействию занятости</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/integracii/kod-buduschego" target="_blank">Код будущего</a>
      </div>
    </div>

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#EEEDFE">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#3C3489" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy" target="_blank">Частые вопросы</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kak-otklonit-zayavku" target="_blank">Как отклонить заявку?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kak-vosstanovit-zayavku" target="_blank">Как восстановить заявку?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kak-menyayutsya-etapy-v-zayavke-i-shagi-v-lk-slushatelya-podrobno" target="_blank">Как меняются этапы в заявке?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kakie-roli-dostupny-vo-flow-crm" target="_blank">Какие роли доступны?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kak-dobavit-pole-s-dop-dannymi-dop-dokument-vsem" target="_blank">Как добавить доп. поле всем заявкам?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/dolgo-gruzitsya-chto-proverit" target="_blank">Долго грузится. Что проверить?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/chasto-zadavaemye-voprosy/kak-slushatel-zagruzit-dop-dokument" target="_blank">Как слушатель загрузит доп. документ?</a>
      </div>
    </div>

    <div class="sd-card">
      <div class="sd-card-head">
        <div class="sd-card-icon" style="background:#FAEEDA">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#854F0B" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
        </div>
        <a class="sd-card-title" href="https://www.flow-crm.study/helpcrm/instrukcii" target="_blank">Инструкции</a>
      </div>
      <div class="sd-links">
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-proiskhodit-onlain-oplata" target="_blank">Как организована оплата?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-rabotat-s-tegami-v-zayavkakh" target="_blank">Как работать с тегами?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-rabotat-s-vneshnimi-istochniki" target="_blank">Как работать с внешними источниками?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-rabotat-s-dopolnitelnymi-polyami" target="_blank">Как работать с доп. полями?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/zamena-dopolnitelnykh-dokumentov" target="_blank">Как работать с доп. документами?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-sdelat-rassylku" target="_blank">Как сделать рассылку?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/instrukcii/kak-massovo-skachat-dokumenty-zayavok-potoka" target="_blank">Как массово скачать документы?</a>
        <a class="sd-link" href="https://www.flow-crm.study/helpcrm/avtomaticheskie-uvedomleniya-sistemy/avtomaticheskie-uvedomleniya" target="_blank">Автоматические уведомления</a>
      </div>
    </div>

  </div>
</div></p>

[/html]