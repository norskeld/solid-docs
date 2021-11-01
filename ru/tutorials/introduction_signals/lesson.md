_Сигналы_ являются краеугольным камнем реактивности Solid. Они содержат значения, которые меняются со временем; когда вы меняете значение Сигнала, он автоматически обновляет все, что его использует.

Чтобы создать Сигнал, давайте импортируем `createSignal` из `solid-js` и вызовем его из нашего компонента `Counter`:

```jsx
const [count, setCount] = createSignal(0);
```

Аргумент, переданный `createSignal`, — это начальное значение, а возвращаемое значение — это массив с двумя функциями: [геттером](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/get) и [сеттером](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/set). С помощью [деструктуризации](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) мы можем называть эти функции как угодно. В этом случае мы называем геттер `count`, а сеттер - `setCount`.

Важно отметить, что первое возвращаемое значение - это геттер (функция, возвращающая текущее значение), а не само значение. Это потому, что фреймворк должен отслеживать, где этот Сигнал считывается, чтобы он мог соответствующим образом всё обновлять.

В этом уроке мы будем использовать функцию JavaScript `setInterval` для создания периодически увеличивающегося счетчика. Мы можем обновлять наш Сигнал `count` каждую секунду, добавив этот код в наш компонент `Counter`:

```jsx
setInterval(() => setCount(count() + 1), 1000);
```

Каждый шаг мы читаем предыдущее значение счетчика, прибавляем к нему 1 и устанавливаем новое.

> Сигналы Solid также принимают такую форму функции, в которой вы можете использовать предыдущее значение для установки следующего значения.
>
> ```jsx
> setCount(c => c + 1);
> ```

Наконец, нам нужно считать Сигнал в нашем JSX-коде:

```jsx
return <div>Count: {count()}</div>;
```