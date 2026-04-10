---
description: >-
  Во Flow есть отличия в количестве и этапности шагов в ЛК слушателя, касающиеся
  группы шаблонов документов, оплаты и генерации договоров со слушателями
order: 2
title: Как меняются этапы в заявке и шаги в ЛК слушателя? (подробно)
---

Во Flow есть отличия в количестве и этапах  в ЛК слушателя, в зависимости от количества групп шаблонов документов (если в программе не установлена группа «по умолчанию»), оплаты, получаемого на выходе документа  и загрузки договоров со слушателями.

Подробнее можно посмотреть на схеме, выбрав нужные параметры в верхнем блоке.

[html]

<style>
.etz * { box-sizing: border-box; }
.etz { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; font-size: 14px; color: #2C2C2A; padding: 8px 0; }
.etz .controls { display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 12px; margin-bottom: 20px; padding: 16px; background: #F5F5F3; border-radius: 12px; border: 0.5px solid #D3D1C7; }
@media(max-width:640px){ .etz .controls { grid-template-columns: 1fr 1fr; } }
.etz .label { font-size: 11px; color: #888780; margin-bottom: 8px; text-transform: uppercase; letter-spacing: .05em; font-weight: 500; }
.etz .toggle-group { display: flex; flex-direction: column; gap: 5px; }
.etz .toggle-btn { padding: 8px 12px; border-radius: 8px; border: 1.5px solid #D3D1C7; background: #fff; color: #5F5E5A; cursor: pointer; font-size: 13px; transition: all .15s; font-family: inherit; text-align: left; line-height: 1.3; box-shadow: 0 1px 3px rgba(0,0,0,.07); }
.etz .toggle-btn.active { background: #1D9E75; border-color: #1D9E75; color: #fff; font-weight: 500; box-shadow: 0 2px 6px rgba(29,158,117,.25); }
.etz .toggle-btn:hover:not(.active) { border-color: #B4B2A9; background: #FAFAF8; box-shadow: 0 1px 4px rgba(0,0,0,.12); }
.etz .legend { display: flex; gap: 14px; flex-wrap: wrap; margin-bottom: 14px; }
.etz .legend-item { display: flex; align-items: center; gap: 5px; font-size: 12px; color: #5F5E5A; }
.etz .legend-dot { width: 12px; height: 12px; border-radius: 50%; flex-shrink: 0; }
.etz .steps-list { display: flex; flex-direction: column; gap: 4px; }
.etz .step { display: flex; align-items: flex-start; gap: 10px; padding: 8px 12px; border-radius: 8px; background: #F5F5F3; }
.etz .step-num { width: 24px; height: 24px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 12px; font-weight: 500; flex-shrink: 0; margin-top: 1px; }
.etz .step-num.base { background: #EEEDFE; color: #3C3489; }
.etz .step-num.pay  { background: #FAEEDA; color: #633806; }
.etz .step-num.docs { background: #E1F5EE; color: #085041; }
.etz .step-num.end  { background: #E1F5EE; color: #085041; border: 1.5px solid #1D9E75; }
.etz .step-text { font-size: 14px; color: #2C2C2A; line-height: 1.4; }
.etz .step-sub { font-size: 12px; color: #5F5E5A; margin-top: 2px; }
.etz .note { font-size: 12px; color: #5F5E5A; padding: 8px 12px; border-left: 2px solid #1D9E75; margin-top: 12px; }
</style>

<div class="etz">
  <div class="controls">
    <div>
      <div class="label">Групп шаблонов</div>
      <div class="toggle-group">
        <button class="toggle-btn active" onclick="etzSet('tmpl','one',this)">Одна</button>
        <button class="toggle-btn" onclick="etzSet('tmpl','many',this)">Несколько</button>
      </div>
    </div>
    <div>
      <div class="label">Договор со слушателем</div>
      <div class="toggle-group">
        <button class="toggle-btn active" onclick="etzSet('dogovor','no',this)">Нет</button>
        <button class="toggle-btn" onclick="etzSet('dogovor','yes',this)">Да</button>
      </div>
    </div>
    <div>
      <div class="label">Тип обучения</div>
      <div class="toggle-group">
        <button class="toggle-btn active" onclick="etzSet('type','cert',this)">С сертификатом<span style="display:block;font-size:11px;font-weight:400;opacity:.8;margin-top:2px">уровень образования ниже заявленного в программе</span></button>
        <button class="toggle-btn" onclick="etzSet('type','qual',this)">С документом о квалификации<span style="display:block;font-size:11px;font-weight:400;opacity:.8;margin-top:2px">уровень образования равен/выше заявленного в программе</span></button>
      </div>
    </div>
    <div>
      <div class="label">Доп. документы в программе</div>
      <div class="toggle-group">
        <button class="toggle-btn active" onclick="etzSet('dopdoc','no',this)">Нет</button>
        <button class="toggle-btn" onclick="etzSet('dopdoc','opt',this)">Есть необязательные</button>
        <button class="toggle-btn" onclick="etzSet('dopdoc','yes',this)">Есть обязательные</button>
      </div>
    </div>
  </div>

  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:#EEEDFE;border:1px solid #AFA9EC"></div>Базовый шаг</div>
    <div class="legend-item"><div class="legend-dot" style="background:#FAEEDA;border:1px solid #EF9F27"></div>Оплата</div>
    <div class="legend-item"><div class="legend-dot" style="background:#E1F5EE;border:1px solid #5DCAA5"></div>Документы / зачисление</div>
  </div>

  <div id="etz-steps"></div>
</div>

<script>
(function(){
const s = {tmpl:'one', dogovor:'no', type:'cert', dopdoc:'no'};

const TAIL = [
  {t:'Зачисление',c:'end'},
  {t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},
  {t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'},
];

const ORIG = {t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'};

const DOPDOC_STEPS_OPT = [
  {t:'Заполнение доп. полей и загрузка доп. документов',s:'Необязательные — если слушатель их заполнил и загрузил',c:'docs'},
  {t:'Проверка доп. полей и документов',s:'Если заполнены и загружены слушателем',c:'docs'},
];
const DOPDOC_STEPS_REQ = [
  {t:'Заполнение доп. полей и загрузка доп. документов',s:'Обязательные поля и документы из программы',c:'docs'},
  {t:'Проверка доп. полей и документов',c:'docs'},
];

function insertAfter(steps, afterTitle, inserts) {
  const idx = steps.findIndex(s => s.t === afterTitle);
  if (idx === -1) return steps;
  return [...steps.slice(0, idx+1), ...inserts, ...steps.slice(idx+1)];
}

function getSteps() {
  const {tmpl, dogovor, type, dopdoc} = s;
  const withDog = dogovor === 'yes';
  const many = tmpl === 'many';
  const qual = type === 'qual';

  const zayvNoDog = [
    {t:'Оформление заявления на зачисление',s:'Загрузка согласия и заявления',c:'docs'},
    {t:'Проверка документов',s:'Согласие и заявление',c:'docs'},
  ];
  const zayvWithDog = [
    {t:'Оформление заявления на зачисление',s:'Загрузка согласия, заявления и договора',c:'docs'},
    {t:'Проверка документов',s:'Согласие, заявление и договор',c:'docs'},
  ];
  const zayv = withDog ? zayvWithDog : zayvNoDog;

  const qualDocs = [
    {t:'Уточнение персональных данных',s:'Загрузка скана паспорта',c:'docs'},
    {t:'Уточнение образования',s:'Загрузка скана документа о текущем образовании',c:'docs'},
    {t:'Проверка документов',s:'Паспорт и документ о текущем образовании',c:'docs'},
  ];

  let steps;

  if (!qual) {
    if (many && !withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Ожидаем одобрения заявки',s:'Организация устанавливает в заявке группу шаблонов',c:'base'},
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        {t:'Выбор периода обучения',c:'base'},
        {t:'Уточнение персональных данных',c:'base'},
        ...zayv, ORIG,
      ];
    } else if (many && withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Ожидаем одобрения заявки',s:'Организация устанавливает в заявке группу шаблонов',c:'base'},
        {t:'Выбор периода обучения',c:'base'},
        {t:'Уточнение персональных данных',c:'base'},
        ...zayv,
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        ORIG,
      ];
    } else if (!many && !withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        {t:'Выбор периода обучения',c:'base'},
        {t:'Уточнение персональных данных',c:'base'},
        ...zayv, ORIG,
      ];
    } else {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Выбор периода обучения',c:'base'},
        {t:'Уточнение персональных данных',c:'base'},
        ...zayv,
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        ORIG,
      ];
    }
  } else {
    if (many && !withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Ожидаем одобрения заявки',s:'Организация устанавливает в заявке группу шаблонов',c:'base'},
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        {t:'Выбор периода обучения',c:'base'},
        ...qualDocs, ...zayv, ORIG,
      ];
    } else if (many && withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Ожидаем одобрения заявки',s:'Организация устанавливает в заявке группу шаблонов',c:'base'},
        {t:'Выбор периода обучения',c:'base'},
        ...qualDocs, ...zayv,
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        ORIG,
      ];
    } else if (!many && !withDog) {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        {t:'Выбор периода обучения',c:'base'},
        ...qualDocs, ...zayv, ORIG,
      ];
    } else {
      steps = [
        {t:'Включить уведомления',c:'base'},
        {t:'Определить тип обучения',c:'base'},
        {t:'Выбор периода обучения',c:'base'},
        ...qualDocs, ...zayv,
        {t:'Оплата обучения',s:'Если обучение бесплатное — пропускается',c:'pay'},
        ORIG,
      ];
    }
  }

  if (dopdoc === 'opt') {
    steps = insertAfter(steps, 'Уточнение персональных данных', DOPDOC_STEPS_OPT);
  } else if (dopdoc === 'yes') {
    steps = insertAfter(steps, 'Уточнение персональных данных', DOPDOC_STEPS_REQ);
  }

  return [...steps, ...TAIL];
}

window.etzSet = function(key, val, btn) {
  s[key] = val;
  btn.closest('.toggle-group').querySelectorAll('.toggle-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  etzRender();
};

function etzRender() {
  const steps = getSteps();
  const needDocs = s.type === 'qual';
  let html = '<div class="steps-list">';
  steps.forEach((step, i) => {
    html += `<div class="step"><div class="step-num ${step.c}">${i+1}</div><div><div class="step-text">${step.t}</div>${step.s?`<div class="step-sub">${step.s}</div>`:''}</div></div>`;
  });
  html += '</div>';
  html += `<div class="note">${needDocs?'Требуются сканы паспорта и документа о текущем образовании':'Сканы паспорта и документа о текущем образовании не требуются'}</div>`;
  document.getElementById('etz-steps').innerHTML = html;
}

etzRender();
})();
</script>

[/html]