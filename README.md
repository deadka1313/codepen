# codepen
Набор ссылок на мои программы на codepen

# 2018 август
Жучок убегает и догоняет курсор умышки, можно менять скорость и его поведение, размеры поля и жучка
***
https://codepen.io/deadka1313/pen/gdMXoZ
***
Похожая программа на жучка, только проще и имеет ускорение и замедление жучка
***
https://codepen.io/deadka1313/pen/XPKNjw
***
Suppose you have an array of integers, both positive and negative, in no particular order.  Find the largest possible sum of any continuous subarray.  
***
For example, if you have all positive numbers, the largest sum would be the sum of the whole array; if you have all negative numbers, the largest sum is 0 (the null subarray)
***
https://codepen.io/deadka1313/pen/mGePrj
***
Write a listbox-style binary search for an ordered array of integers.  Listbox-style means that you should return the index of the first item greater than or equal to the item being searched for; if all items are less, you should return the index of the last item.  You are guaranteed that there is at least one item in the array.
***
https://codepen.io/deadka1313/pen/JaYojP
***
// С бекенда приходит массив такого вида:
var arr = [
  { name: 'width', value: 10 }, 
  { name: 'height', value: 20 },
  // ...
];

// Нужно получить объект такого вида:
/*
{
  width: 10,
  height: 20,
  ...
}
*/

function objFromArr(arr) {
  // code here
  const returnObject = {}
  for (let i = 0; i < arr.length; i++) { 
      returnObject[arr[i].name] = arr[i].value;
  }
  return returnObject;
}


//-------------


var i = 10;
var array = [];

while (i--) {
    const buffer = i;
    array.push(function() {
    	return buffer + buffer;
    });
}

console.log([
    array[0](),
    array[1](),
])


// [18, 16]


//------------



/**
 * Необходимо написать функцию, которая на вход принимает урл, 
 * асинхронно ходит по этому урлу GET запросом и возвращает данные (json).
 * Для получении данных можно использовать $.get или fetch.
 * Если во время запроса произошла ошибка, то пробовать запросить ещё 5 раз.
 * Если в итоге информацию получить не удалось, вернуть ошибку "Заданный URL недоступен".
 */
function get(url, count = 0) {
  // code here
    if (count < 5) {
        return fetch(url).then(data => data.json()).catch(() => {
            return get(url, ++count);
        })
    } else {
        throw Error('Заданный URL недоступен');
    }
}

get(url)
 .then(res => console.log(res))
 .catch(err => console.error(err))
 
 
 //------------
 
 /**
 * Дана строка, состоящая из букв A-Z:
 * "AAAABBBCCXYZDDDDEEEFFFAAAAAABBBBBBBBBBBBBBBBBBBBBBBBBBBB"
 * Нужно написать функцию RLE, которая на выходе даст строку вида:
 * "A4B3C2XYZD4E3F3A6B28"
 * И сгенерирует любую ошибку, если на вход пришла невалидная строка.
 *
 * Пояснения:
 * 1. Если символ встречается 1 раз, он остается без изменений
 * 2. Если символ повторяется более 1 раза, к нему добавляется количество повторений
 */


// AAABB -> A3B2
// A -> A
// AAAB


// 'A' x 'Z'

function rle(str) {
    // your code
        if (/A-Z/.test(str[i])) {
            throw Error('Невалидная строка') 
        }
    let newStr = str[0];
        let count = 1;
    for(let i = 1; i < str.length; i++) {
        if (str[i] === str[i - 1]) {
            count++;
        } else {
            newStr = newStr + (count !== 1 ? count : '') + str[i]; 
            count = 1;
                    }
    
            }
            newStr = newStr + (count !== 1 ? count : '');
    return newStr;
}



// ------



var b = {};
var c;

b.b = 1;
c = b;
c.b = 2;

console.log('1)', b.b); // ? 2
console.log('2)', c.b); // ? 2

var a = { counter: 1 };
function inc(obj) {
    obj.counter++;
    obj.changed = true;
}

inc(a);
console.log('3)', a);   // ? { counter: 2, changed: true }

var d = 'test';
d.d = 1;
console.log('4)', d.d); // ? 1

//d.d -> String(d).d = 1; d.d new String(d).d = ? => undefined

