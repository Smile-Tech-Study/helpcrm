---
order: 0.144574
title: Обучение
---

[html]

<style>
.ob*{box-sizing:border-box}
.ob{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;font-size:14px;color:#2C2C2A;padding:8px 0}
.ob-intro{font-size:14px;color:#5F5E5A;line-height:1.6;margin-bottom:24px}
.ob-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
@media(max-width:540px){.ob-grid{grid-template-columns:1fr}}
.ob-card{border:0.5px solid #D3D1C7;border-radius:12px;background:#fff;padding:20px;display:flex;flex-direction:column;gap:10px}
.ob-card-icon{width:36px;height:36px;border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0;background:#E6F1FB}
.ob-card-title{font-size:16px;font-weight:500;color:#2C2C2A}
.ob-card-desc{font-size:13px;color:#5F5E5A;line-height:1.5;flex:1}
.ob-card-links{display:flex;flex-direction:column;gap:4px;margin-top:4px}
.ob-link{font-size:12px;padding:5px 10px;border-radius:8px;border:0.5px solid #B5D4F4;color:#185FA5;text-decoration:none;background:#E6F1FB;text-align:center;transition:all .15s;display:block}
.ob-link:hover{background:#B5D4F4;color:#0C447C}
</style>

<div class="ob">
  <div class="ob-intro">
    В этом разделе описана структура учебного процесса во Flow — как организованы программы, потоки и приказы, и как они связаны между собой.
  </div>

  <div class="ob-grid">
    <div class="ob-card">
      <div class="ob-card-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"/>
        </svg>
      </div>
      <div class="ob-card-title">Программа</div>
      <div class="ob-card-desc">Образовательная программа — основа учебного процесса. Содержит тип обучения, уровень образования, стоимость и выдаваемый документ. К программе привязываются потоки и шаблоны документов.</div>
      <div class="ob-card-links">
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma" target="_blank">Программа →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma/tipy-programm-i-urovni-obrazovaniya" target="_blank">Типы программ и уровни образования →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Programma/stoimost-programmy" target="_blank">Стоимость программы →</a>
      </div>
    </div>

    <div class="ob-card">
      <div class="ob-card-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/>
        </svg>
      </div>
      <div class="ob-card-title">Поток</div>
      <div class="ob-card-desc">Поток — конкретный период обучения по программе с фиксированными датами старта и окончания. Слушатель выбирает поток при подаче заявки. У потока есть лимит слушателей.</div>
      <div class="ob-card-links">
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Potok" target="_blank">Поток →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/Potok/eksport-dlya-fis-frdo" target="_blank">Экспорт для ФИС ФРДО →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/slushateli/zayavki/zavershenie-obucheniya" target="_blank">Завершение обучения →</a>
      </div>
    </div>

    <div class="ob-card">
      <div class="ob-card-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/>
        </svg>
      </div>
      <div class="ob-card-title">Приказы</div>
      <div class="ob-card-desc">Приказы на зачисление и отчисление фиксируют факт начала и завершения обучения. Выпускаются вручную или автоматически — в зависимости от настроек группы шаблонов.</div>
      <div class="ob-card-links">
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz" target="_blank">Приказы →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz/dobavlenie-prikazov-vruchnuyu" target="_blank">Ручной выпуск →</a>
        <a class="ob-link" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz/avtomaticheskii-vypusk" target="_blank">Автоматический выпуск →</a>
    
      </div>
    </div>
  </div>
</div>

[/html]