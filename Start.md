---
order: 0.10637
title: Быстрый старт
---

* [x] Зарегистрируйте [организацию](./Organization/sozdanie-organizacii) и заполните ее карточку. При добавлении организации Вы автоматически будете зарегистрированы как ее сотрудник.

* [x] Подключите [эквайринг](./instrukcii/kak-proiskhodit-onlain-oplata) при необходимости

* [x] Добавьте [сотрудников](./sotrudniki) и назначьте им роли

* [x] Получите [токен](./Organization/Token/_index) для возможности создания заявок и работы с ними

* [x] Создайте лендинг для размещения [формы сбора заявок](./Organization/Token/forma-sbora-zayavok-na-saite-organizacii) или разместите ее на имеющемся сайте

* [x] Внесите данные [подписантов](./Organization/podpisanty)

* [x] Создавайте [шаблоны документов](./Organization/Shablony/_index), подключайте при необходимости автоматические [приказы](./obuchenie/prikaz/_index) и генерацию договоров

* [x] Добавляйте и редактируйте [программы](./obuchenie/Programma/_index), укажите [стоимость](./obuchenie/Programma/stoimost-programmy)

* [x] Добавьте [потоки](./obuchenie/Potok/_index)

* [x] Работайте с [заявками](./slushateli/zayavki/_index)

* [x] [Завершите обучение](./slushateli/zayavki/zavershenie-obucheniya)

[html]

<p><style>
.bs*{box-sizing:border-box}
.bs{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;font-size:14px;color:#2C2C2A;padding:8px 0}
.bs-phases{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:20px}
@media(max-width:540px){.bs-phases{grid-template-columns:repeat(2,1fr)}}
.bs-phase-btn{padding:12px 8px;border-radius:12px;border:0.5px solid #D3D1C7;background:#F5F5F3;cursor:pointer;text-align:center;transition:all .15s;font-family:inherit}
.bs-phase-btn:hover:not(.active){border-color:#B4B2A9;background:#fff}
.bs-phase-btn.active{border-width:2px}
.bs-phase-num{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:500;margin:0 auto 8px}
.bs-phase-title{font-size:13px;font-weight:500;line-height:1.3;color:#2C2C2A}
.bs-phase-sub{font-size:11px;color:#888780;margin-top:3px}
.bs-content{border:0.5px solid #D3D1C7;border-radius:12px;background:#fff;padding:20px 24px}
.bs-steps{display:flex;flex-direction:column;gap:6px}
.bs-step{display:flex;align-items:flex-start;gap:12px;padding:10px 14px;border-radius:8px;background:#F5F5F3}
.bs-step-num{width:22px;height:22px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:500;flex-shrink:0;margin-top:1px}
.bs-step-body{flex:1}
.bs-step-title{font-size:14px;color:#2C2C2A;font-weight:500;line-height:1.4}
.bs-step-desc{font-size:12px;color:#5F5E5A;margin-top:2px;line-height:1.5}
.bs-links{display:flex;flex-wrap:wrap;gap:4px;margin-top:6px}
.bs-link{font-size:11px;padding:2px 8px;border-radius:10px;border:0.5px solid #B5D4F4;color:#185FA5;text-decoration:none;background:#E6F1FB;cursor:pointer}
.bs-link:hover{background:#B5D4F4;color:#0C447C}
.bs-badge{display:inline-block;font-size:10px;padding:2px 7px;border-radius:10px;margin-left:6px;vertical-align:middle;font-weight:500}
.bs-badge.req{background:#E1F5EE;color:#085041}
.bs-badge.opt{background:#F1EFE8;color:#5F5E5A}
.bs-nav{display:flex;justify-content:space-between;align-items:center;margin-top:18px;padding-top:14px;border-top:0.5px solid #D3D1C7}
.bs-nav-btn{padding:6px 14px;border-radius:8px;border:0.5px solid #B4B2A9;background:#fff;color:#5F5E5A;cursor:pointer;font-size:13px;font-family:inherit;transition:all .15s}
.bs-nav-btn:hover{background:#F5F5F3}
.bs-nav-btn.primary{color:#fff;background:#185FA5;border-color:#185FA5}
.bs-nav-btn:disabled{opacity:.3;cursor:default}
.bs-progress{font-size:12px;color:#888780}
</style>

<div class="bs">
  <div class="bs-phases" id="bs-phases"></div>
  <div class="bs-content" id="bs-content"></div>
</div>

<script>
(function(){
const base='https://www.flow-crm.study/helpcrm';
const phases=[
  {
    title:'Организация',sub:'шаг 1',
    color:'#185FA5',bg:'#E6F1FB',border:'#85B7EB',
    steps:[
      {n:'1',req:true,title:'Зарегистрируйте организацию',desc:'Перейдите на страницу регистрации и заполните данные. Регистрирующий сотрудник автоматически становится администратором.',links:[{t:'Создание организации',u:base+'/Organization/sozdanie-organizacii'}]},
      {n:'2',req:true,title:'Заполните карточку организации',desc:'Реквизиты, лицензия, контакты, подразделение. Данные используются при генерации документов — важно заполнить точно.',links:[{t:'Создание организации',u:base+'/Organization/sozdanie-organizacii'}]},
      {n:'3',req:true,title:'Добавьте подписантов',desc:'Сотрудники, чьи данные будут подставляться в документы.',links:[{t:'Подписанты',u:base+'/Organization/podpisanty'}]},
      {n:'4',req:false,title:'Добавьте сотрудников и назначьте роли',desc:'Пригласите коллег и настройте уровни доступа.',links:[{t:'Сотрудники',u:base+'/sotrudniki'},{t:'Какие роли доступны?',u:base+'/chasto-zadavaemye-voprosy/kakie-roli-dostupny-vo-flow-crm'}]},
      {n:'5',req:false,title:'Подключите эквайринг',desc:'Если планируется онлайн-оплата через ЛК слушателя — подайте заявку на подключение Т-Банка в карточке организации.',links:[{t:'Как организована оплата обучения?',u:base+'/instrukcii/kak-proiskhodit-onlain-oplata'}]},
    ]
  },
  {
    title:'Настройка шаблонов и программ',sub:'шаг 2',
    color:'#0C447C',bg:'#B5D4F4',border:'#378ADD',
    steps:[
      {n:'1',req:true,title:'Создайте шаблоны документов',desc:'Заявления, договоры, приказы. Настройте ключевые слова для автоподстановки данных.',links:[{t:'Шаблоны документов',u:base+'/Organization/Shablony'},{t:'Ключевые слова',u:base+'/Organization/Shablony/klyuchevye-slova'},{t:'Создание шаблонов',u:base+'/Organization/Shablony/sozdanie-sobstvennykh-shablonov'}]},
      {n:'2',req:true,title:'Добавьте программы',desc:'Укажите тип, уровень образования, стоимость и документ, выдаваемый по итогам.',links:[{t:'Программа',u:base+'/obuchenie/Programma'},{t:'Стоимость программы',u:base+'/obuchenie/Programma/stoimost-programmy'}]},
      {n:'3',req:true,title:'Создайте потоки',desc:'Укажите период обучения и лимит слушателей.',links:[{t:'Поток',u:base+'/obuchenie/Potok'}]},
    ]
  },
  {
    title:'Настройка сбора заявок',sub:'шаг 3',
    color:'#042C53',bg:'#E6F1FB',border:'#378ADD',
    steps:[
      {n:'1',req:true,title:'Получите токен организации',desc:'Необходим для связи формы на сайте с системой Flow.',links:[{t:'Токен организации',u:base+'/Organization/Token'}]},
      {n:'2',req:false,title:'Разместите форму сбора заявок',desc:'На сайте организации или лендинге — передаёт данные напрямую во Flow.',links:[{t:'Форма сбора заявок',u:base+'/Organization/Token/forma-sbora-zayavok-na-saite-organizacii'},{t:'Пример на Tilda',u:base+'/Organization/Token/forma-sbora-zayavok-na-primere-tilda'}]},
      {n:'3',req:false,title:'Настройте внешние источники',desc:'Если требуется передавать дополнительные данные вместе с заявкой — промокоды, коды партнёров и т.д.',links:[{t:'Внешние источники',u:base+'/Organization/vneshnie-istochniki'},{t:'Как работать с внешними источниками?',u:base+'/instrukcii/kak-rabotat-s-vneshnimi-istochniki'}]},
      {n:'4',req:false,title:'Настройте дополнительные поля и документы',desc:'Если требуется собирать дополнительные данные от слушателя через ЛК.',links:[{t:'Доп. документы и поля',u:base+'/Organization/dopolnitelnye-dokumenty-i-polya-vvoda-dannykh'},{t:'Как работать с доп. полями?',u:base+'/instrukcii/kak-rabotat-s-dopolnitelnymi-polyami'},{t:'Как работать с доп. документами',u:base+'/instrukcii/zamena-dopolnitelnykh-dokumentov'}]},
    ]
  },
  {
    title:'Работа с заявками и документами',sub:'шаг 4',
    color:'#185FA5',bg:'#B5D4F4',border:'#85B7EB',
    steps:[
      {n:'1',req:true,title:'Принимайте и обрабатывайте заявки',desc:'Следите за статусами — система подскажет что требуется от менеджера на каждом этапе.',links:[{t:'Заявки',u:base+'/slushateli/zayavki'},{t:'Этапы работы с заявкой',u:base+'/slushateli/zayavki/etapy-raboty-s-zayavkoi'},{t:'Способы создания заявок',u:base+'/slushateli/zayavki/sposoby-sozdaniya-zayavok'}]},
      {n:'2',req:true,title:'Проверяйте документы слушателей',desc:'Анкета, паспорт, документ об образовании, документы на зачисление.',links:[{t:'Документы в заявке',u:base+'/slushateli/zayavki/nabor-dokumentov-sobiraemyy-v-sisteme'},{t:'Что заполняет слушатель в ЛК',u:base+'/slushateli/zayavki/polya'}]},
      {n:'3',req:true,title:'Контролируйте оплату',desc:'Через эквайринг в ЛК слушателя или вручную в карточке заявки.',links:[{t:'Как организована оплата обучения?',u:base+'/instrukcii/kak-proiskhodit-onlain-oplata'}]},
      {n:'4',req:true,title:'Завершайте обучение',desc:'После завершения — загрузите документ о квалификации. Статус заявки изменится автоматически.',links:[{t:'Завершение обучения',u:base+'/slushateli/zayavki/zavershenie-obucheniya'}]},
      {n:'5',req:false,title:'Используйте теги и фильтры',desc:'Для удобной работы с большим количеством заявок.',links:[{t:'Как работать с тегами?',u:base+'/instrukcii/kak-rabotat-s-tegami-v-zayavkakh'}]},
    ]
  },
];

let cur=0;

function render(){
  document.getElementById('bs-phases').innerHTML=phases.map((p,i)=>`
    <button class="bs-phase-btn${i===cur?' active':''}" onclick="bsGo(${i})"
      style="${i===cur?`border-color:${p.border};background:${p.bg}`:''}">
      <div class="bs-phase-num" style="background:${i===cur?p.color:'#fff'};color:${i===cur?'#fff':'#888780'};border:0.5px solid ${i===cur?p.color:'#D3D1C7'}">
        ${i+1}
      </div>
      <div class="bs-phase-title" style="${i===cur?`color:${p.color}`:''}">
        ${p.title}
      </div>
      <div class="bs-phase-sub">${p.sub}</div>
    </button>
  `).join('');

  const p=phases[cur];
  document.getElementById('bs-content').innerHTML=`
    <div style="margin-bottom:14px">
      <span style="font-size:11px;text-transform:uppercase;letter-spacing:.05em;font-weight:500;color:${p.color}">Шаг ${cur+1} из ${phases.length}</span>
    </div>
    <div class="bs-steps">
      ${p.steps.map(s=>`
        <div class="bs-step">
          <div class="bs-step-num" style="background:${p.bg};color:${p.color}">${s.n}</div>
          <div class="bs-step-body">
            <div class="bs-step-title">
              ${s.title}
              <span class="bs-badge ${s.req?'req':'opt'}">${s.req?'обязательно':'по необходимости'}</span>
            </div>
            <div class="bs-step-desc">${s.desc}</div>
            <div class="bs-links">
              ${s.links.map(l=>`<a class="bs-link" href="${l.u}" target="_blank">${l.t} →</a>`).join('')}
            </div>
          </div>
        </div>
      `).join('')}
    </div>
    <div class="bs-nav">
      <button class="bs-nav-btn" onclick="bsGo(${cur-1})" ${cur===0?'disabled':''}>← Назад</button>
      <span class="bs-progress">${cur+1} / ${phases.length}</span>
      <button class="bs-nav-btn primary" onclick="bsGo(${cur+1})" ${cur===phases.length-1?'disabled':''}>Далее →</button>
    </div>
  `;
}

window.bsGo=function(i){if(i<0||i>=phases.length)return;cur=i;render();};
render();
})();
</script></p>

[/html]