<h1 align="center">Backend for Kittynotes</h1>

<p>На данный момент описание API неполное и дополняется по мере возможности.
Также оно может изменено в любой момент из-за постоянного добавления нового кода и переписывания старого.</p>
<p>На данный момент API работает нестабильно</p>

<h3 align="center">Описание API</h3>
<h4>1)Регистрация</h4>
<b>Запрос</b>: POST Запрос на <a href = kaplaan.ru/backend/app/api/v1/auth/registration>kaplaan.ru/backend/app/api/v1/auth/registration<a> <br>
<b>Тело запроса</b>: Тело запроса должно состоять из JSON вида:
{
 "email": "....",
 "login": "....",
 "password": "....."
} <br>
Логин и пароль должны быть больше 6 символов, а email должно подходить под паттерн email. Все аргументы обязательные <br>

<b>Коды ответов и их значения</b>: <br>
<ul>
  <li> 400 - BAD REQUEST - Данные, отправленные пользователем не прошли валидацию
  </li>
  
  <li> 401 - UNAUTHORIZED - Пользователь уже зарегистрирован
  </li>
  
  <li> 200 - OK - Ссылка на подтверждение отправлена на почту, введенную пользователем
  </li>
 </ul> <br>
 
 <b>Тело ответа</b>: В качестве тела ответа приходит поясняющее сообщение, которое зависит от кода ответа. <br>
 <hr>
 
 <h4>2)Вход</h4>
<b>Запрос</b>: POST Запрос на <a href = kaplaan.ru/backend/app/api/v1/auth/login>kaplaan.ru/backend/app/api/v1/auth/login<a> <br>
<b>Тело запроса</b>: Тело запроса должно состоять из JSON вида:
{
 "email": "....",
 "login": "....",
 "password": "....."
} <br>
Логин и пароль должны быть больше 6 символов, а email должно подходить под паттерн email. Обязательными аргументами являются email или login и password.
Также к моменту отправки запроса должен быть активирован аккаунт пользователя с помощью email<br>

<b>Коды ответов и их значения</b>: <br>
<ul>
  <li> 400 - BAD REQUEST - Данные, отправленные пользователем не прошли валидацию
  </li>
  
  <li> 401 - UNAUTHORIZED - Пользователь с такими данными не найден или аккаунт не активирован.
  </li>
  
  <li> 200 - OK - Пользователь успешно авторизировался.
  </li>
 </ul> <br>
 
 <b>Тело ответа</b>: В качестве тела ответа приходят jwt access token и jwt refresh token в случае успешной авторизации.
