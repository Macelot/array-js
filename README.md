
# Operações de Array em JavaScript

As operações de array em JavaScript são vastas e poderosas, permitindo manipular e trabalhar com coleções de dados de diversas maneiras. Aqui estão as principais categorias e operações com exemplos:

## 1. Criação de Arrays:

* **Literal:**
    ```javascript
    let arrayLiteral = [1, 2, 3, "a", "b", true];
    ```
* **Construtor `Array`:**
    ```javascript
    let arrayConstrutor = new Array(10); // Cria um array com 10 posições vazias
    let arrayConstrutorComValores = new Array(1, 2, 3);
    ```
* **`Array.of()`:** Cria um novo array com um número variável de argumentos.
    ```javascript
    let arrayOf = Array.of(1, 2, 3); // [1, 2, 3]
    let arrayOfString = Array.of("hello"); // ["hello"]
    let arraySingleNumber = Array.of(5); // [5]
    ```
* **`Array.from()`:** Cria um novo array a partir de um objeto iterable ou array-like.
    ```javascript
    let arrayFromString = Array.from("abc"); // ["a", "b", "c"]
    let setFromArray = Array.from(new Set([1, 2, 2, 3])); // [1, 2, 3]
    // Exemplo com NodeList (requer ambiente de navegador)
    // let nodeList = document.querySelectorAll("div");
    // let arrayFromNodeList = Array.from(nodeList);
    let arrayLike = { length: 2, 0: "foo", 1: "bar" };
    let arrayFromLike = Array.from(arrayLike); // ["foo", "bar"]
    let arrayFromMapping = Array.from([1, 2, 3], x => x * 2); // [2, 4, 6]
    ```

## 2. Acesso e Modificação de Elementos:

* **Acesso por índice:**
    ```javascript
    let arr = [10, 20, 30];
    console.log(arr[0]); // 10
    console.log(arr[1]); // 20
    ```
* **Modificação por índice:**
    ```javascript
    arr[2] = 40;
    console.log(arr); // [10, 20, 40]
    ```
* **`length`:** Propriedade que retorna ou define o número de elementos.
    ```javascript
    console.log(arr.length); // 3
    arr.length = 5; // Adiciona posições vazias
    console.log(arr); // [10, 20, 40, empty × 2]
    arr.length = 2; // Remove elementos do final
    console.log(arr); // [10, 20]
    ```

## 3. Adicionar e Remover Elementos:

* **`push(...elements)`:** Adiciona ao final e retorna o novo `length`.
    ```javascript
    let arr = [1, 2];
    arr.push(3); // Retorna 3
    console.log(arr); // [1, 2, 3]
    arr.push(4, 5); // Retorna 5
    console.log(arr); // [1, 2, 3, 4, 5]
    ```
* **`pop()`:** Remove o último e retorna o elemento removido.
    ```javascript
    let arr = [1, 2, 3];
    let last = arr.pop(); // last é 3
    console.log(arr); // [1, 2]
    ```
* **`unshift(...elements)`:** Adiciona ao início e retorna o novo `length`.
    ```javascript
    let arr = [2, 3];
    arr.unshift(1); // Retorna 3
    console.log(arr); // [1, 2, 3]
    arr.unshift(-1, 0); // Retorna 5
    console.log(arr); // [-1, 0, 1, 2, 3]
    ```
* **`shift()`:** Remove o primeiro e retorna o elemento removido.
    ```javascript
    let arr = [1, 2, 3];
    let first = arr.shift(); // first é 1
    console.log(arr); // [2, 3]
    ```
* **`splice(start, deleteCount, ...items)`:** Altera o conteúdo removendo/substituindo e/ou adicionando. Retorna array dos removidos.
    ```javascript
    let arr = [1, 2, 3, 4, 5];
    let removed = arr.splice(2, 1); // Remove 1 a partir do índice 2 (o 3)
    console.log(arr); // [1, 2, 4, 5]
    console.log(removed); // [3]

    arr.splice(1, 0, 1.5, 1.8); // Adiciona no índice 1
    console.log(arr); // [1, 1.5, 1.8, 2, 4, 5]

    removed = arr.splice(3, 2, "a", "b"); // Remove e adiciona
    console.log(arr); // [1, 1.5, 1.8, "a", "b", 5]
    console.log(removed); // [2, 4]
    ```

## 4. Iteração de Arrays:

* **`for` loop:**
    ```javascript
    let arr = [10, 20, 30];
    for (let i = 0; i < arr.length; i++) {
      console.log(arr[i]);
    }
    ```
* **`for...of` loop:** (ES6)
    ```javascript
    let arr = [10, 20, 30];
    for (const value of arr) {
      console.log(value);
    }
    ```
* **`forEach(callback(element, index, array), thisArg)`:**
    ```javascript
    let arr = [10, 20, 30];
    arr.forEach((element, index) => {
      console.log(`Índice ${index}: ${element}`);
    });
    ```
* **`map(callback(element, index, array), thisArg)`:** Cria um novo array com os resultados.
    ```javascript
    let arr = [1, 2, 3];
    let doubled = arr.map(x => x * 2); // [2, 4, 6]
    ```
* **`filter(callback(element, index, array), thisArg)`:** Cria um novo array com elementos que passam no teste.
    ```javascript
    let arr = [1, 2, 3, 4, 5];
    let even = arr.filter(x => x % 2 === 0); // [2, 4]
    ```
* **`reduce(callback(accumulator, currentValue, currentIndex, array), initialValue)`:** Reduz o array a um único valor.
    ```javascript
    let arr = [1, 2, 3, 4];
    let sum = arr.reduce((acc, curr) => acc + curr, 0); // 10
    ```
* **`reduceRight(callback(...), initialValue)`:** Similar a `reduce()`, mas da direita para a esquerda.
* **`every(callback(...), thisArg)`:** Testa se todos os elementos passam no teste.
    ```javascript
    let arr = [2, 4, 6];
    let allEven = arr.every(x => x % 2 === 0); // true
    ```
* **`some(callback(...), thisArg)`:** Testa se pelo menos um elemento passa no teste.
    ```javascript
    let arr = [1, 3, 5, 2];
    let hasEven = arr.some(x => x % 2 === 0); // true
    ```

## 5. Encontrar Elementos:

* **`indexOf(searchElement, fromIndex)`:** Primeiro índice do elemento ou -1.
    ```javascript
    let arr = [10, 20, 30, 20];
    console.log(arr.indexOf(20)); // 1
    console.log(arr.indexOf(20, 2)); // 3
    console.log(arr.indexOf(40)); // -1
    ```
* **`lastIndexOf(searchElement, fromIndex)`:** Último índice do elemento ou -1.
    ```javascript
    let arr = [10, 20, 30, 20];
    console.log(arr.lastIndexOf(20)); // 3
    ```
* **`includes(searchElement, fromIndex)`:** Retorna `true` se o array contém o elemento.
    ```javascript
    let arr = [1, 2, 3];
    console.log(arr.includes(2)); // true
    console.log(arr.includes(4)); // false
    ```
* **`find(callback(...), thisArg)`:** Retorna o *valor* do primeiro elemento que satisfaz o teste.
    ```javascript
    let arr = [10, 15, 20, 25];
    let found = arr.find(x => x > 12); // 15
    let notFound = arr.find(x => x > 30); // undefined
    ```
* **`findIndex(callback(...), thisArg)`:** Retorna o *índice* do primeiro elemento que satisfaz o teste.
    ```javascript
    let arr = [10, 15, 20, 25];
    let foundIndex = arr.findIndex(x => x > 12); // 1
    let notFoundIndex = arr.findIndex(x => x > 30); // -1
    ```

## 6. Ordenação e Reversão:

* **`sort(compareFunction)`:** Ordena o array *in place*.
    ```javascript
    let arr1 = [3, 1, 4, 1, 5, 9];
    arr1.sort(); // [1, 1, 3, 4, 5, 9] (ordenação de string padrão)
    arr1.sort((a, b) => a - b); // [1, 1, 3, 4, 5, 9] (numérica crescente)
    arr1.sort((a, b) => b - a); // [9, 5, 4, 3, 1, 1] (numérica decrescente)
    // Ordenando array de objetos
    let arr3 = [{ value: 2 }, { value: 1 }, { value: 3 }];
    arr3.sort((a, b) => a.value - b.value);
    console.log(arr3); // [{ value: 1 }, { value: 2 }, { value: 3 }]
    ```
* **`reverse()`:** Inverte a ordem dos elementos *in place*.
    ```javascript
    let arr = [1, 2, 3];
    arr.reverse(); // [3, 2, 1]
    ```

## 7. Outras Operações:

* **`concat(...arrays)`:** Retorna um novo array concatenado.
    ```javascript
    let arr1 = [1, 2];
    let arr2 = [3, 4];
    let arr3 = [5, 6];
    let combined = arr1.concat(arr2, arr3); // [1, 2, 3, 4, 5, 6]
    ```
* **`slice(begin, end)`:** Retorna uma cópia superficial de uma porção do array.
    ```javascript
    let arr = [1, 2, 3, 4, 5];
    let sliced1 = arr.slice(1, 3); // [2, 3]
    let sliced2 = arr.slice(2); // [3, 4, 5]
    let sliced3 = arr.slice(-2); // [4, 5]
    let sliced4 = arr.slice(); // Cópia superficial
    ```
* **`join(separator)`:** Retorna uma string com todos os elementos unidos.
    ```javascript
    let arr = ["apple", "banana", "cherry"];
    let joined1 = arr.join(); // "apple,banana,cherry"
    let joined2 = arr.join(" - "); // "apple - banana - cherry"
    let joined3 = arr.join(""); // "applebananacherry"
    ```
* **`toString()`:** Retorna uma string representando o array (internamente chama `join(',')`).
    ```javascript
    let arr = [1, 2, "a"];
    console.log(arr.toString()); // "1,2,a"
    ```
* **`toLocaleString(locales, options)`:** Retorna uma string localizada representando os elementos.

Dominar essas operações é fundamental para trabalhar eficientemente com arrays em JavaScript. Lembre-se da diferença entre métodos que modificam o array original (*in place*) e aqueles que retornam um novo array.
