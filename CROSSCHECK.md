# Критерии оценки заданий

## Task 1. Caesar cipher CLI tool

Каждый пункт **10 баллов**, частичная реализация пункта **5 баллов**.
Каждый коммит после дедлайна (за исключением коммитов в README.md) **минус 10 баллов**

1. в корне репозитория создана папка с произвольным названием (например caesar-cipher-cli, task1 и т.п.), в которой расположены файлы с кодом программы
2. в README.md должно быть описано, как можно запустить программу из командной строки, описаны аргументы, которые можно передать приложению
3. если переданы все аргументы, приложение читает из файла и записывает в файл зашифрованный/расшифрованный текст, при этом предыдущие записи не удаляются
4. если не переданы обязательные аргументы, приложение передает соответствующее сообщение в process.stderr и прoцесс завершается с кодом, отличным от 0
5. если переданы аргументы с путями к файлам, но файлы отсутствуют (или к ним невозможен доступ), приложение передает соответствующее сообщение в process.stderr и прoцесс завершается с кодом, отличным от 0
6. если не передан аргумент с путем до файла на чтение, то чтение осуществляется из process.stdin
7. если не передан аргумент с путем до файла на запись, то вывод осуществляется в process.stdout
8. шифруются/дешифруются только латинские буквы, регистр сохраняется, остальные символы не изменяются
9. если текст вводится из консоли, то программа не должна завершаться после выполнения шифровки/дешифровки введенного текста, т.е. должна быть возможность ввести еще текст
10. кодовая база не находится в одном файле, а разделена на файлы в соответствии с выполняемыми задачами (например - функция, преобразующая строку, в отдельном файле, код, создающий transform стрим, в отдельном файле, функция для парсинга и валидации аргументов в отдельном файле и т.п.)

N.B. `console.error` пишет ошибку в `process.stderr`, большинство библиотек для парсинга параметров при ошибке также пишут в `process.stderr`. В VS Code, если запустить приложение в режиме [дебага](https://code.visualstudio.com/docs/editor/debugging), можно увидеть в панели output, что цвет сообщений, выводимых в process.stdout и process.stderr отличаются.

## Task 2. Express REST service

Проверку тестов следует проводить в [Node.js последней LTS версии](https://nodejs.org/en/).
При выставлении оценок используйте [рекомендации RSSchool](https://docs.rs.school/#/cross-check-flow?id=%d0%9f%d1%80%d0%b8%d0%bd%d1%86%d0%b8%d0%bf-%d0%be%d1%86%d0%b5%d0%bd%d0%ba%d0%b8-%d1%80%d0%b0%d0%b1%d0%be%d1%82%d1%8b-%d0%bf%d1%80%d0%b8-cross-check-%d0%bf%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b5).
Минимальная оценка за таску не может быть меньше 0.
Максимально возможная оценка: 170 баллов - 1 пункт, 10 баллов - 3 пункт, 10 баллов - 4 пункт, 10 баллов - 5 пункт, итого: 200 баллов.

1. каждый успешный тест при выполнении скрипта `npm run test` +10 баллов.
2. в тестах не должно быть исправлений, за исключением обновлений из [репозитория RS School](https://github.com/rolling-scopes-school/nodejs-course-template/tree/master). Если есть другие изменения в файлах с тестами, за каждый исправленный тест минус 10 баллов.

  >  **Как обновиться из [репозитория RS School](https://github.com/rolling-scopes-school/nodejs-course-template/tree/master)**
  >  1. Установить VSCode как дефолтный GIT редактор (не обязательный пункт)
  >    ```bash
  >      git config --global core.editor "code --wait"
  >    ```
  >  2. Закомитать текущие изменения
  >  3. Добавить в качестве дополнительного удаленного репозитория темплейт
  >    ```bash
  >      git remote add template https://github.com/rolling-scopes-school/nodejs-course-template.git
  >    ```
  >  4. Применить изменения из темплейта
  >    ```bash
  >      git pull template master --allow-unrelated-histories
  >    ```
  >  5. Применить все свои изменения
  >    ```bash
  >      git checkout --ours ':!node_modules'
  >    ```
  >  6. Применить все изменения для папки `test`
  >    ```bash
  >      git checkout --theirs ./test
  >    ```
  >  7. Сохранить изменения
  >    ```bash
  >      git add .
  >    ```
  >  8. Продолжить мердж
  >    ```bash
  >      git commit
  >    ```
  >  9. Закрыть вкладку VSCode с описанием коммита. Если дефолтный редактор не меняли - выйти из VIM  `:qa`

  > **Как увидеть различия для папки `test` между текущей веткой и веткой master из темплейта**
  >  1. Открыть глобальный `.gitconfig`:
  >    `git config --global -e`
  >  2. Добавить в глобальный `.gitconfig` следующие строки. Если вы не используете VSCode замените `code` на соответстующую вашей IDE команду (или путь к выполняемому файлу).
  >    ```
  >      [diff]
  >        tool = vscode
  >      [difftool "vscode"]
  >        cmd = code --wait --diff $LOCAL $REMOTE
  >    ```
  >  3. Добавить в качестве дополнительного удаленного репозитория темплейт
  >    ```bash
  >      git remote add template https://github.com/rolling-scopes-school/nodejs-course-template.git
  >    ```
  >  4. Создать локальную копию ветки master из темплейта
  >     `git fetch template master:template-master`
  >  5. Запустить сравнение для текущей ветки с веткой master темплейта
  >    `git difftool <название текущей ветки> template-master test/`

3. код приложения, работающий с сущностью user разделен по модулям в соответствии с его назначением (к примеру: работа с запросом и ответом в *.router.js, бизнес-логика в *.service.js, работа с хранилищем данных в *.repository.js и т.п.) + 10 баллов
4. аналогично пункту 3 для boards +10 баллов
5. аналогично пункту 3 для tasks + 10 баллов
6. каждый коммит после дедлайна минус 10 баллов.

## Task 3. Logging & Error Handling

При выставлении оценок используйте [рекомендации RSSchool](https://docs.rs.school/#/cross-check-flow?id=%d0%9f%d1%80%d0%b8%d0%bd%d1%86%d0%b8%d0%bf-%d0%be%d1%86%d0%b5%d0%bd%d0%ba%d0%b8-%d1%80%d0%b0%d0%b1%d0%be%d1%82%d1%8b-%d0%bf%d1%80%d0%b8-cross-check-%d0%bf%d1%80%d0%be%d0%b2%d0%b5%d1%80%d0%ba%d0%b5).

Максимальная оценка - 100 баллов.

1. реализовано логирование (url, query parameters, body) для всех запросов к серверу с использованием middleware +20 баллов
2. добавлена централизованная обработка всех ошибок, которая включает отправку респонса с соответствующим кодом http статуса и их логирование с использованием middleware +20 баллов
3. добавлены обработка и логирование ошибок на событие `uncaughtException` +20 баллов
4. добавлены обработка и логирование ошибок на событие `unhandledRejection` +20 баллов
5. процесс логирования осуществляется единственным модулем +20 баллов
6. каждый коммит после дедлайна минус 10 баллов.

Все тесты `npm run test` должны проходить, если не проходят тесты минус 10 баллов.
