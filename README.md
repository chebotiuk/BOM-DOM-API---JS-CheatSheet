# BOM-DOM-API---JS-CheatSheet
JS CheatSheet for DOM and BOM API

Написать в док-те (работает только при загрузке стр-ци)
```
document.write("abc"); // (можно поместить в любое место html в теге 'script')
document.writeln("abc"); // (пишет в линию, корректно работает в теге <pre>)
```

// Общ. св-ва
document.cookie // св-во позволяет читать и писать куки файлы
document.lastModified // дата последнего изменения док-та
document.location // устаревший синоним св-ва url
document.referrer // адрес док-та содержащего ссылку кот привела на этот документ
document.title // содержимое html тега <title>

document.anchors // коллекция якорей док-та
document.forms // коллекция форм док-та
document.images // коллекция картинок док-та
document.links // коллекция ссылок док-та

// Селлекторы
document.getElementById('#id') // получить эл по id
document.getElementsByTagName('tag') // получить коллекцию эл-тов по тегам
document.getElementsByName('name') // получить коллекцию эл-тов по атр name
document.getElementsByClassName('class') // получить коллекцию эл-тов по атр class
document.querySelectorAll('#id .class tag') // получить коллекцию эл-тов по css селлектору
document.querySelector('#id .class tag') //  получить первый эл-т по css селлектору

// Навигация по узлам
el.childNode // вернет все дочерние ел-ты
el.parentNode // вернет родительский узел
el.firstChild // вернет первый дочерний эл-т
el.lastChild // вернет последний дочерний эл-т
el.nextSibling // вернет след-щего соседа
el.previousSibling // вернет пред-щего соседа
	
	// Альтернатива для получения только эл-тов:
	el.children
	el.parentElement
	el.firstElementChild
	el.lastElementChild
	el.nextElementSibling
	el.previousElementSibling


// Методы для работы с DOM
var par = document.createElement(type, props, children)
document.createTextNode(string) // Creates a new text node with the node value of string.
el.appendChild(par) // Добавить дочерний эл-т
el.insertBefore(newElement, referenceElement) // вставит эл-т newElement перед эл-том referenceElement, кот является childNode of el
el.removeChild(par) // Удаляет дочерний элемент из DOM. Возвращает удаленный элемент.
el.replaceChild(newChild, oldChild) // Заменяет дочерний элемент на выбранный. Возвращает замененный элемент.

el.setAttribute(name, value) // Устанавливает эл-ту атрибут
el.removeAttribute(name) // Удаляем атрибут
el.getAttribute(name) // Получить атрибут



// Получить инфо об узле
el.nodeType // Вернет тип узла, где 1 - Element, 3 - Text, 8 - Comment, 9 - Document
el.nodeName // Вернет имя эл-та по тегу
el.nodeValue // Вернет или запишет текстовое значение узла, альтернатива el.innerText или data
el.innerHTML // Вернет или запишет html узла

// Стили
el.style.color = 'red'; // Задать инлайновый стиль эл-ту
el.style.cssText = 'color: red; margin: 50px;'; // Задать стиль одной строкой

el.className // добавить, или просмотреть классы в виде строки
el.classList.add('className') // Добавить класс эл-ту
el.classList.remove('className') // Удалить класс эл-та
el.classList.toggle('className') // Сдалать туггл класса
el.classList.contains('className') // Проверяет наличие класса у эл-та, вернет true или false

var computedStyle = getComputedStyle(el); // Вернет объект с вычесленными стилями эл-та


// Events (события)
window.onload = function() {};
el.onclick = function() {}; // пример события на эл-те

onClick //Событие выполняется по клику мыши
onLoad  //Событие выполняется, когда загрузился документ, или его часть
onChange //Для чекбоксов. Событие выполняется при изменении их состояния
onMouseOver, onMouseOut // Когда пользователь проводет мышкой над элементом
onMouseDown, onMouseUp  // Событие onClick, поделенное на два этапа, нажатие и отпуск клавиши мыши
onKeyPress, onKeyUp, onKeyDown // Когда происходит нажатие клавиши на клавиатуре
onfocus // Когда выбран в фокусе определенный элемент
onBlur // Когда этот элемент не выбран

// Добавление событий через event listener
el.addEventListener('click', function() {

});