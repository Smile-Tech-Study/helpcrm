---
description: Для работы в системе с данными будущих слушателей создаются заявки
order: 0.3
title: Способы создания заявок
---

[html]

<p><style>
.zc*{box-sizing:border-box}
.zc{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;padding:8px 0}
.zc-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
@media(max-width:560px){.zc-grid{grid-template-columns:1fr}}
.zc-card{border:1.5px solid #D3D1C7;border-radius:12px;background:#fff;padding:16px;cursor:pointer;transition:border-color .15s}
.zc-card:hover{border-color:#378ADD}
.zc-card.open{border-color:#1D9E75}
.zc-card-head{display:flex;align-items:flex-start;gap:12px}
.zc-icon{width:36px;height:36px;border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.zc-card-title{font-size:14px;font-weight:500;color:#2C2C2A;margin-bottom:3px;line-height:1.3}
.zc-card-when{font-size:12px;color:#5F5E5A;line-height:1.4}
.zc-tags{display:flex;flex-wrap:wrap;gap:4px;margin-top:10px}
.zc-tag{font-size:11px;padding:2px 8px;border-radius:10px;font-weight:500}
.zc-expand{overflow:hidden;max-height:0;transition:max-height .3s ease}
.zc-expand.open{max-height:900px}
.zc-divider{border:none;border-top:0.5px solid #D3D1C7;margin:12px 0}
.zc-steps{display:flex;flex-direction:column;gap:5px}
.zc-step{display:flex;align-items:flex-start;gap:9px;padding:8px 12px;border-radius:8px;background:#F5F5F3}
.zc-step-num{width:20px;height:20px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:500;flex-shrink:0;margin-top:1px;background:#E6F1FB;color:#0C447C}
.zc-step-text{font-size:12px;color:#2C2C2A;line-height:1.4}
.zc-step-sub{font-size:11px;color:#5F5E5A;margin-top:1px}
.zc-note{margin-top:10px;padding:8px 12px;border-left:2px solid #5DCAA5;font-size:12px;color:#085041;font-style:italic;line-height:1.5}
.zc-tip{margin-top:8px;padding:8px 12px;border-left:2px solid #AFA9EC;font-size:12px;color:#3C3489;line-height:1.5;background:#EEEDFE;border-radius:0 6px 6px 0}
.zc-warn{margin-top:8px;padding:8px 12px;border-left:2px solid #EF9F27;font-size:12px;color:#633806;line-height:1.5}
.zc-sub-title{font-size:12px;font-weight:500;color:#2C2C2A;margin:12px 0 6px}
.zc-arrow{margin-left:auto;flex-shrink:0;margin-top:2px;width:24px;height:24px;border-radius:50%;background:#F5F5F3;border:0.5px solid #D3D1C7;display:flex;align-items:center;justify-content:center;transition:transform .2s,background .15s}
.zc-card:hover .zc-arrow{background:#E6F1FB;border-color:#85B7EB}
.zc-card.open .zc-arrow{transform:rotate(180deg);background:#E1F5EE;border-color:#5DCAA5}
.zc-wide{grid-column:1/-1}
</style>

<div class="zc">
  <div class="zc-grid" id="zc-grid"></div>
</div>

<script>
(function(){

var chevron='<svg width="12" height="12" viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="2 4 6 8 10 4"/></svg>';

var cards=[
  {
    icon:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#185FA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>',
    ic:'#E6F1FB',
    title:'С сайта / лендинга',
    when:'Слушатель сам записывается через форму на вашем сайте',
    tags:[{t:'Слушатель заполняет сам',c:'#E6F1FB',ct:'#0C447C'},{t:'Нужен сайт',c:'#F1EFE8',ct:'#444441'}],
    steps:[
      {n:1,t:'Получите токен организации',sub:'В карточке организации → вкладка «Информация»'},
      {n:2,t:'Передайте инструкцию администратору сайта',sub:'Для настройки формы приёма заявок'},
      {n:3,t:'Заявки автоматически поступают в Flow'},
      {n:4,t:'Менеджер проверяет документы и одобряет заявки'},
    ],
    warn:'Требует технической настройки формы на сайте разработчиком.'
  },
  {
    icon:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#085041" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>',
    ic:'#E1F5EE',
    title:'Вручную',
    when:'Менеджер вносит одну заявку напрямую в систему',
    tags:[{t:'Менеджер вносит',c:'#E1F5EE',ct:'#085041'},{t:'Одна заявка',c:'#F1EFE8',ct:'#444441'}],
    steps:[
      {n:1,t:'Перейдите в «Заявки» → «Создать заявку»'},
      {n:2,t:'Заполните данные: ФИО, email, телефон'},
      {n:3,t:'Выберите программу и поток'},
      {n:4,t:'Нажмите «Создать заявку»'},
      {n:5,t:'Слушатель получит письмо с доступом в ЛК'},
    ],
    note:'Слушатель может продолжить заполнение данных сам в ЛК.'
  },
  {
    icon:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#633806" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>',
    ic:'#FAEEDA',
    title:'Импорт из Excel',
    when:'Массовое создание заявок из заполненного файла',
    tags:[{t:'Менеджер вносит',c:'#E1F5EE',ct:'#085041'},{t:'Много заявок',c:'#FAEEDA',ct:'#633806'}],
    steps:[
      {n:1,t:'«Заявки» → «Создать заявку» → «Импорт заявок»'},
      {n:2,t:'Скачайте шаблон Excel-файла'},
      {n:3,t:'Заполните данные слушателей в файле'},
      {n:4,t:'Выберите программу и загрузите файл'},
      {n:5,t:'Нажмите «Импортировать»'},
    ],
    note:'Все заявки создадутся одновременно. Слушатели получат письма с доступом в ЛК.',
    tip:'В шаблон импорта можно добавить колонки для дополнительных полей и внешних источников — данные сразу попадут в карточки заявок. Колонки должны совпадать с ключевыми словами настроенных полей.'
  },
  {
    icon:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#3C3489" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>',
    ic:'#EEEDFE',
    title:'Через Odin',
    when:'Слушатель уже зарегистрирован в Odin — его нужно связать с Flow',
    tags:[{t:'Интеграция с Odin',c:'#EEEDFE',ct:'#3C3489'},{t:'Ручная связка',c:'#F1EFE8',ct:'#444441'}],
    steps:[
      {n:1,t:'Создайте пользователя во Flow с той же почтой что в Odin',sub:'Кнопка «+» на странице «Пользователи»'},
      {n:2,t:'Профили свяжутся автоматически'},
      {n:3,t:'Программа и поток должны совпадать в обеих системах'},
    ],
    warn:'Если студент добавлен в группу в Odin, во Flow он автоматически не появится — нужна ручная связка.'
  },
  {
    wide:true,
    icon:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#712B13" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="8" y1="6" x2="21" y2="6"/><line x1="8" y1="12" x2="21" y2="12"/><line x1="8" y1="18" x2="21" y2="18"/><line x1="3" y1="6" x2="3.01" y2="6"/><line x1="3" y1="12" x2="3.01" y2="12"/><line x1="3" y1="18" x2="3.01" y2="18"/></svg>',
    ic:'#FAECE7',
    title:'С дополнительными данными',
    when:'Нужно собрать дополнительную информацию от слушателей — через ЛК или через форму на сайте',
    tags:[{t:'Доп. поля в ЛК',c:'#FAECE7',ct:'#712B13'},{t:'Внешние источники',c:'#F1EFE8',ct:'#444441'}],
    sections:[
      {
        title:'Дополнительные поля — слушатель заполняет в ЛК',
        steps:[
          {n:1,t:'Карточка организации → «Дополнительные данные» → «Добавить новое поле»'},
          {n:2,t:'Укажите название, формат ввода и ключевое слово (на английском)'},
          {n:3,t:'Сохраните — поле появится в ЛК слушателя на шаге заполнения данных'},
        ],
        note:'Поля создаются ДО начала сбора заявок. Слушатели сами заполняют их в ЛК, данные отображаются в карточке заявки.'
      },
      {
        title:'Внешние источники — данные из формы на сайте',
        steps:[
          {n:1,t:'Карточка организации → «Внешние источники» → добавьте источник'},
          {n:2,t:'Укажите название и короткое имя на английском'},
          {n:3,t:'Добавьте поле с этим именем в код формы на сайте'},
        ],
        note:'Данные из внешних источников видны только сотрудникам организации — например, для передачи промокода или UTM-метки.'
      }
    ]
  },
];

function renderSteps(steps){
  var h='<div class="zc-steps">';
  steps.forEach(function(s){
    h+='<div class="zc-step"><div class="zc-step-num">'+s.n+'</div><div>';
    h+='<div class="zc-step-text">'+s.t+'</div>';
    if(s.sub)h+='<div class="zc-step-sub">'+s.sub+'</div>';
    h+='</div></div>';
  });
  return h+'</div>';
}

var openIdx=-1;

function render(){
  var html='';
  cards.forEach(function(c,i){
    var isOpen=openIdx===i;
    html+='<div class="zc-card'+(isOpen?' open':'')+(c.wide?' zc-wide':'')+'" onclick="zcToggle('+i+')">';
    html+='<div class="zc-card-head">';
    html+='<div class="zc-icon" style="background:'+c.ic+'">'+c.icon+'</div>';
    html+='<div style="flex:1"><div class="zc-card-title">'+c.title+'</div><div class="zc-card-when">'+c.when+'</div></div>';
    html+='<div class="zc-arrow" style="color:'+(isOpen?'#085041':'#888780')+'">'+chevron+'</div>';
    html+='</div>';
    html+='<div class="zc-tags">';
    c.tags.forEach(function(t){html+='<span class="zc-tag" style="background:'+t.c+';color:'+t.ct+'">'+t.t+'</span>';});
    html+='</div>';
    html+='<div class="zc-expand'+(isOpen?' open':'')+'">';
    html+='<hr class="zc-divider">';
    if(c.sections){
      c.sections.forEach(function(sec,si){
        if(si>0)html+='<hr class="zc-divider">';
        html+='<div class="zc-sub-title">'+sec.title+'</div>';
        html+=renderSteps(sec.steps);
        if(sec.note)html+='<div class="zc-note">'+sec.note+'</div>';
      });
    } else {
      html+=renderSteps(c.steps);
      if(c.warn)html+='<div class="zc-warn">'+c.warn+'</div>';
      if(c.note)html+='<div class="zc-note">'+c.note+'</div>';
      if(c.tip)html+='<div class="zc-tip">'+c.tip+'</div>';
    }
    html+='</div>';
    html+='</div>';
  });
  document.getElementById('zc-grid').innerHTML=html;
}

window.zcToggle=function(i){openIdx=openIdx===i?-1:i;render();};
render();
})();
</script></p>

[/html]

[Как работать с доп.полями?](./../../../instrukcii/kak-rabotat-s-dopolnitelnymi-polyami/_index)

[Как работать с внешними источниками?](./../../../instrukcii/kak-rabotat-s-vneshnimi-istochniki)

## Видеоинструкция

[video:https://rutube.ru/video/f5d3cd9e6401a0f8bafe6b521a4251d2/]