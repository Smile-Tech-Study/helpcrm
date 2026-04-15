---
title: Приказы
order: 0.46
---

:::info 

Приказы фиксируют факт зачисления слушателя на обучение и его отчисления по итогам.

:::

### **Типы приказов**

В системе Flow представлены **2 типа приказов**:

-  **Приказы на зачисление -** слушатель зачислен на обучение

-  **Приказы об отчислении**:

   -  Заявление слушателя - слушатель отчислен по собственному желанию

   -  Неуспеваемость - слушатель не завершил обучение успешно

   -  Выдача документа о квалификации / сертификата - слушатель успешно завершил обучение (с выдачей документа о квалификации)

### Способы выпуска

Выпускаются двумя способами (зависит от настроек [группы шаблонов](./../../Organization/Shablony/_index)):

-  [**автоматически**](./avtomaticheskii-vypusk)  (также доступен [**автоматический режим с ручными корректировками**](./avtomaticheskii-vypusk))

-  [**вручную**](./dobavlenie-prikazov-vruchnuyu).

:::tip 

Подробнее в интрактивном виджете

:::

[html]

<style>
.pw*{box-sizing:border-box}
.pw{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;padding:8px 0}
.pw-controls{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:12px;margin-bottom:20px;padding:16px;background:#F5F5F3;border-radius:12px;border:0.5px solid #D3D1C7}
@media(max-width:640px){.pw-controls{grid-template-columns:1fr 1fr}}
.pw-label{font-size:11px;color:#888780;margin-bottom:8px;text-transform:uppercase;letter-spacing:.05em;font-weight:500}
.pw-group{display:flex;gap:6px;flex-wrap:wrap}
.pw-btn{padding:8px 14px;border-radius:8px;border:1.5px solid #D3D1C7;background:#fff;color:#2C2C2A;cursor:pointer;font-size:12px;transition:all .15s;font-family:inherit;line-height:1.3;box-shadow:0 1px 3px rgba(0,0,0,.08)}
.pw-btn:hover:not(.active){border-color:#185FA5;background:#E6F1FB;color:#0C447C}
.pw-btn.active{background:#185FA5;border-color:#0C447C;color:#fff;font-weight:500;box-shadow:0 2px 6px rgba(24,95,165,.25)}
.pw-result{border:0.5px solid #D3D1C7;border-radius:12px;background:#fff;padding:20px 24px}
.pw-steps{display:flex;flex-direction:column;gap:6px;margin-bottom:12px}
.pw-step{display:flex;align-items:flex-start;gap:10px;padding:9px 14px;border-radius:8px;background:#F5F5F3}
.pw-step-num{width:22px;height:22px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:500;flex-shrink:0;margin-top:1px}
.pw-step-text{font-size:13px;color:#2C2C2A;line-height:1.4}
.pw-step-sub{font-size:11px;color:#5F5E5A;margin-top:2px}
.pw-warn{padding:8px 12px;border-left:2px solid #EF9F27;font-size:12px;color:#633806;margin-top:10px}
.pw-note{padding:8px 12px;border-left:2px solid #5DCAA5;font-size:12px;color:#085041;margin-top:8px;font-style:italic}
</style>

<div class="pw">
  <div class="pw-controls">

    <div>
      <div class="pw-label">Режим выпуска</div>
      <div class="pw-group">
        <button class="pw-btn active" onclick="pwSet('mode','auto',this)">Автоматический</button>
        <button class="pw-btn" onclick="pwSet('mode','manual',this)">Ручной</button>
      </div>
    </div>

    <div id="pw-launch-col">
      <div class="pw-label">Как запустить</div>
      <div class="pw-group">
        <button class="pw-btn active" onclick="pwSet('launch','night',this)">Запускается сам (ночью перед днём старта потока)</button>
        <button class="pw-btn" onclick="pwSet('launch','potok',this)">Вручную со страницы потока (если требуется установить свой номер)</button>
      </div>
    </div>

    <div>
      <div class="pw-label">Тип приказа</div>
      <div class="pw-group">
        <button class="pw-btn active" onclick="pwSet('ptype','enroll',this)">На зачисление</button>
        <button class="pw-btn" onclick="pwSet('ptype','dismiss',this)">На отчисление</button>
      </div>
    </div>

    <div id="pw-reason-col" style="display:none">
      <div class="pw-label">Основание</div>
      <div class="pw-group">
        <button class="pw-btn active" onclick="pwSet('reason','success',this)">Успешное завершение</button>
        <button class="pw-btn" onclick="pwSet('reason','fail',this)">Неуспеваемость</button>
        <button class="pw-btn" onclick="pwSet('reason','own',this)">По заявлению</button>
      </div>
    </div>

  </div>
  <div id="pw-result" class="pw-result"></div>
</div>

<script>
(function(){

var st = {mode:'auto', launch:'night', ptype:'enroll', reason:'success'};

var sc = {
  'auto-night-enroll': {label:'Автоматический — ночной запуск — зачисление',lc:'#0C447C',title:'Приказ генерируется автоматически в день старта потока',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'В группе шаблонов установите галочку «Автоматически» в разделе приказов'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Убедитесь что слушателям одобрили ДЗС до старта потока',s:'Заявление, согласие на обработку ПД, договор (если требуется)'},
    {n:3,bg:'#E1F5EE',c:'#085041',t:'В 00:30 мск в день старта потока система сгенерирует приказ',s:'Все слушатели с одобренными ДЗС попадут в один приказ'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Приказ автоматически прикрепится к заявкам слушателей'},
  ],note:'Для слушателей с поздним зачислением система ежедневно создаёт отдельные приказы с новыми номерами (ПЗ-2, ПЗ-3...).'},

  'auto-night-dismiss-success': {label:'Автоматический — ночной запуск — успешное завершение',lc:'#085041',title:'Приказ генерируется ночью после дня завершения обучения',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'В группе шаблонов установите галочку «Автоматически» в разделе приказов'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Дождитесь окончания потока и выставьте статус «Завершил успешно»',s:'На странице потока — «Завершить обучение» или через Odin'},
    {n:3,bg:'#E1F5EE',c:'#085041',t:'Ночью система сгенерирует приказ',s:'Все слушатели со статусом «Завершил успешно» попадут в один приказ'},
  ],note:'Если позже появились новые слушатели со статусом — система создаст отдельный приказ с новым номером.'},

  'auto-night-dismiss-fail': {label:'Автоматический — ночной запуск — неуспеваемость',lc:'#633806',title:'Приказ генерируется ночью после дня завершения обучения',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'В группе шаблонов установите галочку «Автоматически» в разделе приказов'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Дождитесь окончания потока и выставьте статус «Не завершил обучение»',s:'На странице потока — «Завершить обучение» или через Odin'},
    {n:3,bg:'#E1F5EE',c:'#085041',t:'Ночью система сгенерирует приказ за неуспеваемость'},
  ],warn:'Слушатель с заявлением по собственному желанию не попадёт в приказ за неуспеваемость — для него выпускается отдельный приказ.'},

  'auto-night-dismiss-own': {label:'Автоматический — ночной запуск — по заявлению',lc:'#4A1B0C',title:'Приказ генерируется в день одобрения заявления',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'В группе шаблонов установите галочку «Автоматически» в разделе приказов'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Слушатель загружает заявление на отчисление в ЛК'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Менеджер одобряет заявление в карточке заявки'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'В этот же день система автоматически выпустит приказ'},
  ],warn:'Отчислить по заявлению можно только до даты окончания обучения.'},

  'auto-potok-enroll': {label:'Автоматический — со страницы потока — зачисление',lc:'#0C447C',title:'Запускаете генерацию досрочно из карточки потока',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Убедитесь что в группе шаблонов стоит галочка «Автоматически»'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Убедитесь что слушателям одобрили ДЗС',s:'Заявление, согласие на обработку ПД, договор (если требуется)'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Откройте карточку потока — «...» — «Сгенерировать приказ на зачисление»'},
    {n:4,bg:'#E6F1FB',c:'#0C447C',t:'Выберите шаблон (если групп несколько), проверьте номер и дату'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Проверьте список слушателей — только те у кого одобрены ДЗС'},
    {n:6,bg:'#E1F5EE',c:'#085041',t:'Нажмите «Сгенерировать»'},
  ],note:'Для слушателей с поздним зачислением запустите генерацию повторно — они попадут в отдельный приказ с новым номером.'},

  'auto-potok-dismiss-success': {label:'Автоматический — со страницы потока — успешное завершение',lc:'#085041',title:'Запускаете генерацию досрочно из карточки потока',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Выставьте статус «Завершил успешно» по слушателям',s:'На странице потока — «Завершить обучение» или через Odin'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Откройте карточку потока — «...» — «Сгенерировать приказ на отчисление»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Выберите тип «Успешное завершение», проверьте дату',s:'Дата должна быть в рамках периода обучения потока'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Проверьте список — только слушатели со статусом «Завершил успешно»'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Нажмите «Сгенерировать»'},
  ]},

  'auto-potok-dismiss-fail': {label:'Автоматический — со страницы потока — неуспеваемость',lc:'#633806',title:'Запускаете генерацию досрочно из карточки потока',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Выставьте статус «Не завершил обучение» по слушателям',s:'На странице потока — «Завершить обучение» или через Odin'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Откройте карточку потока — «...» — «Сгенерировать приказ на отчисление»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Выберите тип «Неуспеваемость», проверьте дату',s:'Дата должна быть в рамках периода обучения потока'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Проверьте список — только слушатели со статусом «Не завершил обучение»'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Нажмите «Сгенерировать»'},
  ],warn:'Слушатель с заявлением по собственному желанию не попадёт в этот список.'},

  'auto-potok-dismiss-own': {label:'Автоматический — со страницы потока — по заявлению',lc:'#4A1B0C',title:'Запускаете генерацию досрочно из карточки потока',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Убедитесь что заявление слушателя одобрено в карточке заявки'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Откройте карточку потока — «...» — «Сгенерировать приказ на отчисление»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Выберите тип «По заявлению слушателя», проверьте дату'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Нажмите «Сгенерировать»'},
  ],warn:'Отчислить по заявлению можно только до даты окончания обучения.'},

  'manual-enroll': {label:'Ручной — зачисление',lc:'#0C447C',title:'Создаёте приказ и назначаете слушателям вручную',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'В группе шаблонов установите галочку «Ручной выпуск» в разделе приказов'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Перейдите в «Обучение» — «Приказы» — «Создать»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Заполните: номер, программа, поток, тип «На зачисление», основание, дата'},
    {n:4,bg:'#E6F1FB',c:'#0C447C',t:'Прикрепите скан подписанного приказа (можно добавить позже)'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Откройте карточку заявки на этапе «Требуется выпустить приказ на зачисление» — блок «Обучение» — «Редактировать»'},
    {n:6,bg:'#E1F5EE',c:'#085041',t:'Выберите созданный приказ из списка — «Сохранить»'},
    {n:7,bg:'#E1F5EE',c:'#085041',t:'Повторите шаги 5–6 для каждого слушателя потока'},
  ],note:'Приказ назначается только если в заявке выбрана группа шаблонов с ручным выпуском приказов.'},

  'manual-dismiss-success': {label:'Ручной — успешное завершение',lc:'#085041',title:'Создаёте приказ после завершения обучения',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Перейдите в «Обучение» — «Приказы» — «Создать»'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Тип «На отчисление», основание «Выдача документа о квалификации»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Прикрепите скан приказа'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Откройте заявки на этапе «Требуется загрузить приказ на отчисление»'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Назначьте приказ каждому слушателю через «Обучение» — «Редактировать»'},
  ]},

  'manual-dismiss-fail': {label:'Ручной — неуспеваемость',lc:'#633806',title:'Создаёте приказ после завершения обучения',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Перейдите в «Обучение» — «Приказы» — «Создать»'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Тип «На отчисление», основание «Неуспеваемость»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Прикрепите скан приказа'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Откройте заявки на этапе «Требуется загрузить приказ на отчисление за неуспеваемость»'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Назначьте приказ каждому слушателю через «Обучение» — «Редактировать»'},
  ]},

  'manual-dismiss-own': {label:'Ручной — по заявлению слушателя',lc:'#4A1B0C',title:'Создаёте приказ после одобрения заявления',steps:[
    {n:1,bg:'#E6F1FB',c:'#0C447C',t:'Убедитесь что заявление одобрено в карточке заявки'},
    {n:2,bg:'#E6F1FB',c:'#0C447C',t:'Перейдите в «Обучение» — «Приказы» — «Создать»'},
    {n:3,bg:'#E6F1FB',c:'#0C447C',t:'Тип «На отчисление по заявлению слушателя», прикрепите скан'},
    {n:4,bg:'#E1F5EE',c:'#085041',t:'Откройте карточку заявки — «Требуется загрузить приказ на отчисление (по заявлению)»'},
    {n:5,bg:'#E1F5EE',c:'#085041',t:'Назначьте приказ через «Обучение» — «Редактировать»'},
  ],warn:'Отчислить по заявлению можно только до даты окончания обучения.'},
};

function getKey() {
  if (st.mode === 'manual') {
    return st.ptype === 'enroll' ? 'manual-enroll' : ('manual-dismiss-' + st.reason);
  }
  if (st.ptype === 'enroll') return 'auto-' + st.launch + '-enroll';
  return 'auto-' + st.launch + '-dismiss-' + st.reason;
}

window.pwSet = function(k, v, btn) {
  st[k] = v;
  btn.closest('.pw-group').querySelectorAll('.pw-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  document.getElementById('pw-launch-col').style.display = (st.mode === 'auto') ? 'block' : 'none';
  document.getElementById('pw-reason-col').style.display = (st.ptype === 'dismiss') ? 'block' : 'none';
  render();
};

function switchToPotok() {
  st.launch = 'potok';
  var launchBtns = document.getElementById('pw-launch-col').querySelectorAll('.pw-btn');
  launchBtns.forEach(function(b){ b.classList.remove('active'); });
  launchBtns[1].classList.add('active');
  render();
}

function render() {
  var s = sc[getKey()] || {};
  var stepsHtml = (s.steps || []).map(function(x) {
    return '<div class="pw-step"><div class="pw-step-num" style="background:' + x.bg + ';color:' + x.c + '">' + x.n + '</div><div><div class="pw-step-text">' + x.t + '</div>' + (x.s ? '<div class="pw-step-sub">' + x.s + '</div>' : '') + '</div></div>';
  }).join('');
  document.getElementById('pw-result').innerHTML =
    '<div style="font-size:11px;text-transform:uppercase;letter-spacing:.05em;font-weight:500;color:' + (s.lc||'#185FA5') + ';margin-bottom:8px">' + (s.label||'') + '</div>' +
    '<div style="font-size:17px;font-weight:500;color:#2C2C2A;margin-bottom:16px;line-height:1.3">' + (s.title||'') + '</div>' +
    '<div class="pw-steps">' + stepsHtml + '</div>' +
    (s.warn ? '<div class="pw-warn">' + s.warn + '</div>' : '') +
    (s.note ? '<div class="pw-note">' + s.note + '</div>' : '') +
    (st.mode === 'auto' && st.launch === 'night' ? '<div style="margin-top:12px;padding:10px 14px;border-radius:8px;background:#F5F5F3;font-size:12px;color:#5F5E5A;line-height:1.5">Хотите задать свой номер, дату или выбрать конкретных слушателей? <a id="pw-switch-link" href="https://www.flow-crm.study/helpcrm/obuchenie/prikaz/avtomaticheskii-vypusk#%D0%B0%D0%B2%D1%82%D0%BE%D0%BC%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9-%D1%80%D0%B5%D0%B6%D0%B8%D0%BC-%D1%81-%D1%80%D1%83%D1%87%D0%BD%D1%8B%D0%BC%D0%B8-%D0%BA%D0%BE%D1%80%D1%80%D0%B5%D0%BA%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%BA%D0%B0%D0%BC%D0%B8" style="color:#185FA5;font-size:12px;font-family:inherit" target="_blank" rel="noopener noreferrer">Вручную со страницы потока →</a></div>' : '');
}

render();

document.getElementById('pw-result').addEventListener('click', function(e) {
  if (e.target && e.target.id === 'pw-switch-link') {
    e.preventDefault();
    switchToPotok();
  }
});

})();
</script>

[/html]

---

### Даты в приказах на зачисление

Возможны три варианта генерации приказов на зачисление в зависимости от даты начала обучения. **Дата приказа на зачисление - дата старта потока.**

| **Сценарий**                                                                                                                          | **Дата в приказе**                                                 |
|---------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| Зачисление в день старта потока                                                                                                       | Дата старта потока                                                 |
| Ранний доступ до старта потока (**через кнопку «Записать на обучение в Odin»,** если обучение проходит в Odin)                        | Дата старта потока (приказ выпускается в день старта)              |
| Слушатель с поздним зачислением (после старта потока) (**через кнопку «Записать на обучение в Odin»,** если обучение проходит в Odin) | Дата старта потока (приказ выпускается после одобрения документов) |

## Удаление приказов

:::note 

**Удалить приказ нельзя. Можно заменить скан приказа или перегенерировать приказ (изменить состав слушателей, номер, дату).**

**Если в автоматически сгенерированном приказе остался последний слушатель, то для его удаления исключения обратиться в** [**техническую поддержку**](https://forms.yandex.ru/cloud/65d60d46c417f36a041706d2/)**.**

:::