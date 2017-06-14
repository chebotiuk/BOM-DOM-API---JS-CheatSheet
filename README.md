# JS CheatSheet for DOM and BOM API

**Написать в док-те (работает только при загрузке стр-ци)**
```js
document.write("abc"); // (можно поместить в любое место html в теге 'script')
document.writeln("abc"); // (пишет в линию, корректно работает в теге <pre>)
```

**Общ. св-ва**
```js
document.cookie // св-во позволяет читать и писать куки файлы
document.lastModified // дата последнего изменения док-та
document.location // устаревший синоним св-ва url
document.referrer // адрес док-та содержащего ссылку кот привела на этот документ
document.title // содержимое html тега <title>
```

**Коллекции**
```js
document.anchors // коллекция якорей док-та
document.forms // коллекция форм док-та
document.images // коллекция картинок док-та
document.links // коллекция ссылок док-та
```

**Селлекторы**
```js
document.getElementById('#id') // получить эл по id
document.getElementsByTagName('tag') // получить коллекцию эл-тов по тегам
document.getElementsByName('name') // получить коллекцию эл-тов по атр name
document.getElementsByClassName('class') // получить коллекцию эл-тов по атр class
document.querySelectorAll('#id .class tag') // получить коллекцию эл-тов по css селлектору
document.querySelector('#id .class tag') //  получить первый эл-т по css селлектору
document.documentElement // свойство только для чтения, которое возвращает коренной элемент док-та
```

**Навигация по узлам**
```js
el.childNodes // вернет все дочерние ел-ты
el.parentNode // вернет родительский узел
el.firstChild // вернет первый дочерний эл-т
el.lastChild // вернет последний дочерний эл-т
el.nextSibling // вернет след-щего соседа
el.previousSibling // вернет пред-щего соседа
el.closest('#id .class tag'); // возвращает ближайший родительский элемент (или сам элемент), который соответствует заданному CSS-селектору или null
```

```js
	// Альтернатива для получения только эл-тов (исключая текст. узлы и комменты):
	el.children
	el.parentElement
	el.firstElementChild
	el.lastElementChild
	el.nextElementSibling
	el.previousElementSibling
```


**Методы для работы с DOM**
```js
var frag = document.createDocumentFragment(); // узел-пустышка, используется для миграции включенных в него узлов в основное DOM дерево (применяется для оптимизации производительности);
var el = document.createElement(type, props, children) // Создать новый узел
var txt = document.createTextNode(string) // Создать текстовый узел, где string - текст
var elClone = el.cloneNode(true); // Клонировать узел, если true - то доч узлы включаются
el.appendChild(par) // Добавить дочерний эл-т
el.insertBefore(newElement, referenceElement) // вставит эл-т newElement перед эл-том referenceElement, кот является childNode of el
el.removeChild(par) // Удаляет дочерний элемент из DOM. Возвращает удаленный элемент.
el.replaceChild(newChild, oldChild) // Заменяет дочерний элемент на выбранный. Возвращает замененный элемент.
el.contains(otherNode) // Возвращает true если otherNode является потомком el. В противном случае возвращает false.
el.insertAdjacentHTML(position, text); // Разбирает text как HTML или XML и вставляет полученные узлы (nodes) в DOM дерево относительно el. Варианты position:
										// 'beforebegin' - Перед el; 'afterbegin'- Внутри el, перед первым дочерним эл-том.
										// 'beforeend' - Внутри element, после последнего дочернего эл-та; 'afterend' - После element.


```

**Работа с атрибутами**
```js
el.setAttribute(name, value) // Устанавливает эл-ту атрибут
el.removeAttribute(name) // Удаляем атрибут
el.getAttribute(name) // Получить атрибут
```

**Получить информацию об узле / Запись информации в узел**
```js
el.nodeType // Вернет тип узла, где 1 - Element, 3 - Text, 8 - Comment, 9 - Document
el.nodeName // Вернет имя эл-та по тегу
el.nodeValue // Вернет или запишет текстовое значение текстового узла, альтернатива el.data
el.textContent // Вернет или запишет текстовое значение узла, альтернатива el.innerText
el.innerHTML // Вернет или запишет html узла
el.outerHTML // Аналогичен el.innerHTML, но также включает в себя и html самого el
```

**Стили**
```js
el.style.color = 'red'; // Задать инлайновый стиль эл-ту
el.style.cssText = 'color: red; margin: 50px;'; // Задать стиль одной строкой
var computedStyle = getComputedStyle(el); // Вернет объект с вычесленными стилями эл-та
```

**Классы**
```js
el.className // добавить, или просмотреть классы в виде строки
el.classList.add('className') // Добавить класс эл-ту
el.classList.remove('className') // Удалить класс эл-та
el.classList.toggle('className') // Сдалать туггл класса
el.classList.contains('className') // Проверяет наличие класса у эл-та, вернет true или false
```

**Events (события)**
```js
window.onload = function() {}; // Код сработает при загрузке всего док-та
el.onclick = function() {}; // добавление события через обработчик
el.addEventListener('click', function() {  
	// Добавление событий через event listener
});

// HTML <button class="" onclick='function'>Submit</button> 
// JSX <button className="" onClick='function'>Submit</button>
```

```js
onClick //Событие выполняется по клику мыши
onLoad  //Событие выполняется, когда загрузился документ, или его часть
onChange //Для чекбоксов, инпутов, селлектов... Событие выполняется при изменении их состояния
onInput //Для инпутов. Событие выполняется при вводе нового символа
onMouseOver, onMouseOut // Когда пользователь проводет мышкой над элементом
onMouseDown, onMouseUp  // Событие onClick, поделенное на два этапа, нажатие и отпуск клавиши мыши
onKeyPress, onKeyUp, onKeyDown // Когда происходит нажатие клавиши на клавиатуре
onfocus // Когда поставлен фокус на определенный элемент
onBlur // Когда фокус снят с эл-та
```

**Анимация**
```js
myReq = requestAnimationFrame(callback); // Запустить анимацию
cancelAnimationFrame(myReq);	// Остановить анимацию
```