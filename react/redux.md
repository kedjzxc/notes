https://redux-toolkit.js.org/tutorials/quick-start
--
в больших приложениях вместо контекста стоит использовать redux, чтобы избежать лишнего рендеринга
redux хранит глобальное состояние, то есть в отличие от контекста, при внесении измений в один компонент, другой компонент меняется не сразу, т.е связь между ними не прямая, а между ними есть еще промежуточный элемент, который предоставлен redux'ом (глобальное состояние)
redux-toolkit и react не будут видеть друг друга без react-redux. Изначально мы ипортируем, созданное нами хранилище в index.js, потом импортируем Provider из react-redux и оборачиваем компонент App в Provider и в Provider в качестве значение мы прокидываем store={store}. После этого надо создать слайсы, отвечающие за логику отдельных частей приложения
--
configureStore создает хранилище, в слайсах должен быть объект initialState, после этого создается объект с помощью createSlice, в него передается имя, initialState, и методы, методы записываются в объект reducers, в аргументы методов, которые находятся в reducers передается state, который представляет собой, объявленный раньше объект initialState и action. При экспорте методов мы обращаемся не к reducers, а к actions, т.е const {} = /название слайса/.actions. /Название слайса/.reducer по сути является слайсом и мы экспортируем его по дефолту. Потом с помощью useSelector вытаскиваем state
sdfsdfsdf