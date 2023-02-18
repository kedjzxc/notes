Один из способов делать сетевые запросы это метод fetch:
let promise = fetch(url, [options]) 
url - URL для отправки запроса 
options - дополнительные параметры: метод, заголовки и т.д.
Если не прописывать options, то это обычный get запрос 
Когда запрос выолнен возвращается объект Response. Если мы хотим видеть результат запроса из асинхронной функции, то после вызова функции мы должны использовать на ней метод then()
Пример использования:
fetch('https://jsonplaceholder.typicode.com/todos/1')
.then(res => res.json())
.then(res => console.log(res))
Мы можем выбрать только один метод чтения ответа, т.е если мы получили ответ с response.text(), тогда response.json() не сработает, так как данные уже были обработаны


Для установки заголовка мы можем использовать опцию headers. Она содержит объект с исходящими закголовками, например: 
let response = fetch(protectedUrl, {
  headers: {
    Authentication: 'secret'
  }
});

Для отправки POST-запроса или любого другого, кроме GET мы должны использовать параметры method и body

let user = {
    name: 'John',
    age: 30
}

async function foo() {
    let response = await fetch('https://jsonplaceholder.typicode.com/todos/', 
    {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(user)
    })
    let data = response.json()
    return data
}
--
FormData
--
formdata - это объект, предсталяющий данные HTML-формы, создаваемый с помощью конструктора
let formdata = new FormData([form])
fecth позволяет указать объект formdata в свойстве body

С помощью указанных ниже методов мы можем изменять поля в объекте FormData:

formData.append(name, value) – добавляет к объекту поле с именем name и значением value,
formData.append(name, blob, fileName) – добавляет поле, как будто в форме имеется элемент <input type="file">, третий аргумент fileName устанавливает имя файла (не имя поля формы), как будто это имя из файловой системы пользователя,
formData.delete(name) – удаляет поле с заданным именем name,
formData.get(name) – получает значение поля с именем name,
formData.has(name) – если существует поле с именем name, то возвращает true, иначе false
Технически форма может иметь много полей с одним и тем же именем name, поэтому несколько вызовов append добавят несколько полей с одинаковыми именами.

Ещё существует метод set, его синтаксис такой же, как у append. Разница в том, что .set удаляет все уже имеющиеся поля с именем name и только затем добавляет новое. То есть этот метод гарантирует, что будет существовать только одно поле с именем name, в остальном он аналогичен .append:

formData.set(name, value),
formData.set(name, blob, fileName).
