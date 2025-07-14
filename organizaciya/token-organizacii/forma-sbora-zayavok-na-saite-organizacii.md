# Форма сбора заявок на сайте организации

{% hint style="info" %}
Образовательные организации имеют возможность разместить форму по приёму заявок на своём сайте-лендинге.  После настройки формы заявки будут попадать во  Flow.&#x20;
{% endhint %}

Предложенная ниже инструкция по интеграции подойдет для любого сайта, доступен [пример интеграции на базе сайта на Tilda](forma-sbora-zayavok-na-primere-tilda.md).

**Шаг 1: Получите токен организации**

Для того чтобы получать заявки с вашего лендинга, необходимо сгенерировать токен организации. Токен можно получить следующим образом:

1. Перейдите на страницу вашей [организации](../) во Flow.
2. Найдите кнопку **"**[**Получить токен**](./)**"** и нажмите на неё. При наведении на знак вопроса высветится следующая подсказка:

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

3. "Получить токен" = "Скопировать токен" в буфер обмена,  далее его необходимо будет вставить в value="Ваш токен организации" на шаге 3.

**Шаг 2: Определите ID образовательной программы**

Перед созданием формы, вам необходимо определить ID образовательной программы. Этот ID можно найти на странице программы в вашей системе Flow. Запишите этот ID, он понадобится для настройки формы.

**Шаг 3: Создайте HTML-форму**

Теперь создайте HTML-форму, которую пользователи будут заполнять на вашем сайте. Скопируйте и вставьте следующий код в то место вашего лендинга, где вы хотите разместить форму. Замените `ID программы` на фактический ID образовательной программы:

```
<form  id="requestForm">

<input  type="hidden" name="EducationalProgramId"  value="ID программы">
<input  type="hidden" name="Token" value="Ваш токен организации">

<label  for="firstName">Имя:</label>
<input  type="text"  name="FirstName"  required><br><br>

<label  for="lastName">Фамилия:</label>
<input  type="text"  name="LastName"><br><br>

<label  for="middleName">Отчество:</label>
<input  type="text"  name="MiddleName"><br><br>

<label  for="email">Email:</label>
<input  type="email"  name="Email"  required><br><br>

<label  for="phone">Телефон:</label>
<input  type="tel"  name="Phone"  required><br><br>

<button  type="submit">Отправить</button>

</form>

<div id="responseMessage" style="display:none;"></div>
```

**Шаг 4: Добавьте JavaScript для отправки формы**

Теперь добавим JavaScript-код, который будет отправлять данные формы на сервер и отображать сообщение об успешной отправке. Скопируйте и вставьте следующий код после вашей формы:

```
<script>
    document.getElementById('requestForm').addEventListener('submit', function (event) {
      event.preventDefault(); // Предотвращаем стандартное поведение формы

      const formData = new FormData(this);

      fetch('https://api.flow-crm.study/CitizenRequest/NewCommerceRequest', {
        method: 'POST',
        body: JSON.stringify(Object.fromEntries(formData)),
        headers: {
          'Content-Type': 'application/json'
        }
      })
        .then(response => response.json())
        .then(data => {
          document.getElementById('requestForm').style.display = 'none';
          document.getElementById('responseMessage').innerText = 'Заявка успешно отправлена!';
          document.getElementById('responseMessage').style.display = 'block';
        })
        .catch(error => {
          document.getElementById('responseMessage').innerText = 'Ошибка при отправке заявки.';
          document.getElementById('responseMessage').style.display = 'block';
        });
    });
  </script>
```

**Шаг 5: Проверьте работу формы**

После добавления HTML и JavaScript кода на ваш лендинг, проверьте работу формы. Заполните поля и убедитесь, что данные успешно отправляются, и появляется сообщение об успешной отправке.

На этом всё! Теперь у вас на сайте есть форма для отправки заявок, которая отправляет заявку в вашу Организацию во Flow и отображает сообщение об успешной отправке.

**Шаг 6: Проверьте появление заявки во Flow CRM**

{% embed url="http://rutube.ru/video/private/895c8fd5e2e3352512b5f993d1938e44/?p=LkCVXgsGPb_Hbg98Q_0pLA" %}
