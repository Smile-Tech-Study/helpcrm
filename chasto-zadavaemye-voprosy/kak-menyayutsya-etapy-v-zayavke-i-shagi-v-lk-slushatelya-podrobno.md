---
description: >-
  Во Flow есть отличия в количестве и этапности шагов в ЛК слушателя, касающиеся
  группы шаблонов документов, оплаты и генерации договоров со слушателями
order: 2
title: Как меняются этапы в заявке и шаги в ЛК слушателя? (подробно)
---

Во Flow есть отличия в количестве и этапности шагов в ЛК слушателя, касающиеся группы шаблонов документов, оплаты и генерации договоров со слушателями

[html]

<style>
.etz * { box-sizing: border-box; }
.etz { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; font-size: 14px; color: #2C2C2A; padding: 8px 0; }
.etz .controls { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 16px; margin-bottom: 20px; padding: 16px; background: #F5F5F3; border-radius: 12px; border: 0.5px solid #D3D1C7; }
@media(max-width:560px){ .etz .controls { grid-template-columns: 1fr; } }
.etz .label { font-size: 11px; color: #888780; margin-bottom: 8px; text-transform: uppercase; letter-spacing: .05em; font-weight: 500; }
.etz .toggle-group { display: flex; gap: 6px; flex-wrap: wrap; }
.etz .toggle-btn { padding: 6px 14px; border-radius: 12px; border: 1.5px solid #B4B2A9; background: #fff; color: #5F5E5A; cursor: pointer; font-size: 13px; transition: all .15s; font-family: inherit; text-align: left; line-height: 1.3; }
.etz .toggle-btn.active { background: #1D9E75; border-color: #1D9E75; color: #fff; font-weight: 500; }
.etz .toggle-btn:hover:not(.active) { background: #F1EFE8; }
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
const s = {tmpl:'one', dogovor:'no', type:'cert'};
const sc = {
  'many-no-cert': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Ожидаем одобрения заявки',c:'base'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',c:'base'},{t:'Оформление заявления',s:'Загрузка согласия и заявления',c:'docs'},{t:'Проверка документов',s:'Согласие и заявление',c:'docs'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'many-yes-cert': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Ожидаем одобрения заявки',c:'base'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',c:'base'},{t:'Оформление заявления',s:'Загрузка согласия, заявления и договора',c:'docs'},{t:'Проверка документов',s:'Согласие, заявление и договор',c:'docs'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'one-no-cert': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',c:'base'},{t:'Оформление заявления',s:'Загрузка согласия и заявления',c:'docs'},{t:'Проверка документов',s:'Согласие и заявление',c:'docs'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'one-yes-cert': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',c:'base'},{t:'Оформление заявления',s:'Загрузка согласия, заявления и договора',c:'docs'},{t:'Проверка документов',s:'Согласие, заявление и договор',c:'docs'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'many-no-qual': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Ожидаем одобрения заявки',c:'base'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',s:'Загрузка скана паспорта',c:'docs'},{t:'Уточнение образования',s:'Загрузка скана документа об образовании',c:'docs'},{t:'Проверка документов',s:'Паспорт и документ об образовании',c:'docs'},{t:'Оформление заявления',s:'Загрузка согласия и заявления',c:'docs'},{t:'Проверка документов',s:'Согласие и заявление',c:'docs'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'many-yes-qual': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Ожидаем одобрения заявки',c:'base'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',s:'Загрузка скана паспорта',c:'docs'},{t:'Уточнение образования',s:'Загрузка скана документа об образовании',c:'docs'},{t:'Проверка документов',s:'Паспорт и документ об образовании',c:'docs'},{t:'Оформление заявления',s:'Загрузка согласия, заявления и договора',c:'docs'},{t:'Проверка документов',s:'Согласие, заявление и договор',c:'docs'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'one-no-qual': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',s:'Загрузка скана паспорта',c:'docs'},{t:'Уточнение образования',s:'Загрузка скана документа об образовании',c:'docs'},{t:'Проверка документов',s:'Паспорт и документ об образовании',c:'docs'},{t:'Оформление заявления',s:'Загрузка согласия и заявления',c:'docs'},{t:'Проверка документов',s:'Согласие и заявление',c:'docs'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
  'one-yes-qual': [{t:'Включить уведомления',c:'base'},{t:'Определить тип обучения',c:'base'},{t:'Выбор периода',c:'base'},{t:'Уточнение персональных данных',s:'Загрузка скана паспорта',c:'docs'},{t:'Уточнение образования',s:'Загрузка скана документа об образовании',c:'docs'},{t:'Проверка документов',s:'Паспорт и документ об образовании',c:'docs'},{t:'Оформление заявления',s:'Загрузка согласия, заявления и договора',c:'docs'},{t:'Проверка документов',s:'Согласие, заявление и договор',c:'docs'},{t:'Оплата обучения',s:'если обучение бесплатное — пропускается',c:'pay'},{t:'Отправка оригиналов документов',s:'Если требуется, зависит от настроек программы',c:'docs'},{t:'Зачисление',c:'end'},{t:'Отчисление',s:'Успешно / неуспешно / по собственному желанию',c:'end'},{t:'Выдача документа',s:'Для успешно завершивших обучение',c:'end'}],
};
window.etzSet = function(key, val, btn) {
  s[key] = val;
  btn.closest('.toggle-group').querySelectorAll('.toggle-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  etzRender();
};
function etzRender() {
  const key = `${s.tmpl}-${s.dogovor}-${s.type}`;
  const steps = sc[key] || [];
  const needDocs = s.type === 'qual';
  let html = '<div class="steps-list">';
  steps.forEach((step, i) => {
    html += `<div class="step"><div class="step-num ${step.c}">${i+1}</div><div><div class="step-text">${step.t}</div>${step.s?`<div class="step-sub">${step.s}</div>`:''}</div></div>`;
  });
  html += '</div>';
  html += `<div class="note">${needDocs?'Требуются сканы паспорта и документа об образовании':'Сканы паспорта и документа об образовании не требуются'}</div>`;
  document.getElementById('etz-steps').innerHTML = html;
}
etzRender();
})();
</script>

[/html]