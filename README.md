<div align="center"><h3>Яндекс Карта JS API 3.0</h3></div>

##

<br>
<br>
<p align="center">🔎 Preview on <a href="https://genevy.github.io/yandex-map-api-3/"><strong>GitHub Pages »</strong></a></p>
<br>
<br>

  В начале создаём глобальную переменную "map", присваивая ей значение null. чтобы начать работать с объектом когда он будет создан в функции main()
  
  `window.map = null;`
 
 
    // Главная функция, вызывается при запуске скрипта
    main();
    async function main() {
      // ожидание загрузки модулей
      await ymaps3.ready;
      const {
        YMap,
        YMapDefaultSchemeLayer,
        YMapControls,
        YMapDefaultFeaturesLayer,
        YMapMarker
      } = ymaps3;

      // Импорт модулей для элементов управления на карте
      const {YMapZoomControl, YMapGeolocationControl} = await ymaps3.import('@yandex/ymaps3-controls@0.0.1');

      // Координаты центра карты
      const CENTER_COORDINATES = [37.623082, 55.752540];
      // координаты метки на карте
      const MARKER_COORDINATES = [37.623082, 55.752540];

      // Объект с параметрами центра и зумом карты
      const LOCATION = {center: CENTER_COORDINATES, zoom: 9};

      // Создание объекта карты
      map = new YMap(document.getElementById('map'), {location: LOCATION});

      // Добавление слоев на карту
      map.addChild(scheme = new YMapDefaultSchemeLayer());
      map.addChild(new YMapDefaultFeaturesLayer());

      // Добавление элементов управления на карту
      map.addChild(new YMapControls({position: 'right'})
        .addChild(new YMapZoomControl({}))
      );
      map.addChild(new YMapControls({position: 'top right'})
        .addChild(new YMapGeolocationControl({}))
      );

      // Создание маркера
      const el = document.createElement('img');
      el.className = 'my-marker';
      el.src = './marker.svg';
      el.title = 'Маркер';
      // При клике на маркер меняем центр карты на LOCATION с заданным duration
      el.onclick = () => map.update({location: {...LOCATION, duration: 400}});

      // Создание заголовка маркера
      const markerTitle = document.createElement('div');
      markerTitle.className = 'marker-title';
      markerTitle.innerHTML = 'Заголовок маркера';

      // Контейнер для элементов маркера
      const imgContainer = document.createElement('div');
      imgContainer.appendChild(el);
      imgContainer.appendChild(markerTitle);

      // Добавление центра карты
      map.addChild(new YMapMarker({coordinates: CENTER_COORDINATES}));

      // Добавление маркера на карту
      map.addChild(new YMapMarker({coordinates: MARKER_COORDINATES}, imgContainer));`
      


##
<br>
<div align="center"><p>© Made with care for everyone's use by <a href="https://github.com/genevy">Evgeny Striganov</a></p></div>
      
      
      
