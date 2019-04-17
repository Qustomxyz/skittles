## Чтобы не ждать загрузку большого JS файла

Используем async:

```javascript
<script src="1.js" async></script>
<script src="2.js" async></script>
```

или defer:

```javascript
<script src="1.js" defer></script>
<script src="2.js" defer></script>
```

defer гарантирует порядок запуска скрпитов, async запускает скрипты по мере загрузки.

defer ждет полной загрузки документа и потом запускает скрипты, async запускает скрипты сразу

В современных браузерах при одновременном указании defer и async - всё будет async

Оба атрибута имеют смысл только при src. Если подключения скрипта по src нет, то async/defer браузер игнорирует

Если использовать динамичное добавление скрипта на страницу через возможности JS, то добавляемые скрипты работают как async.

Т.е. если так добавлять несколько зависимых скриптов, то для гарантированного сохранения порядка надо отключить async

Например, так:

```javascript
function addScript(src){
  var script = document.createElement('script');
  script.src = src;
  script.async = false; // чтобы гарантировать порядок
  document.head.appendChild(script);
}

addScript('1.js'); // загружаться эти скрипты начнут сразу
addScript('2.js'); // выполнятся, как только загрузятся
addScript('3.js'); // но, гарантированно, в порядке 1 -> 2 -> 3
```