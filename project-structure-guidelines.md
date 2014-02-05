Это черновик файла с описанием рекомендаций по структуре новых проектов при их
создании.

## Создание нового репозитория с проектом на Lua

При заведении нового репозитория первый коммит должен иметь сообщение
`initial commit` и содержать следующие файлы:
   - .gitignore (копируем из pk-project-tools/src/lua/common.template/)
   - README - содержит название проекта, copyright, ссылку на файл с описанием
     лицензии (описано в гугледокументе "Правила оформления лицензии на код")
   - COPYRIGHT - содержит подробное описание лицензии
     (описано в гугледокументе "Правила оформления лицензии на код")
   - etc/git/hooks/pre-commit - git hook последней версии, принятой для проектов
     (копируем из pk-project-tools/src/lua/common.template/)
   - AUTHORS - содержит список авторов (файл должен присутствовать, если ссылка
     на него присуствует в файле `COPYRIGHT`)
   - HISTORY - содержит список изменений, сгрупированных по версиям (описано в
     гугледокументе "Правила оформления лицензии на код")

`initial commit` обязательно отправляется на ревью (см. [Ревью кода](development-guidelines.md#%D0%A0%D0%B5%D0%B2%D1%8C%D1%8E-%D0%BA%D0%BE%D0%B4%D0%B0)).
Для создания патчсета можно использовать следующую команду:

    git format-patch --root $SHA

$SHA - хэш первого коммита.

Начиная с Git 1.7.12 можно использовать команду:

    git format-patch --root

### Приблизительная структура библиотечного проекта

    <lib-name>/
      etc/
        git/
          hooks/
            pre-commit
        [list-exports/]
          [config.lua]
          [list-exports]
      src/
        <code language>/
          <lib-name>/
            <code-files>.lua
            ...
        ...
      rockspec/
        [gen-rockspecs]
        [pk-rocks-manifest.lua]
        [rockspec.template]
        <lib-name>-<version>.rockspec
        ...
      test/
        cases/
          [0010-<module>.lua]
          [0020-<dir-module>.lua]
          [0030-<module-part>.lua]
          [0031-<module-another_part>.lua]
        [data/]
          [<test-data>]
      COPYRIGHT
      [HISTORY]
      make.sh
      README
      .gitignore

## Прототип на движке Unity 3D

    <git-repo-name>/
      <prototype_name>/
        app/
          Assets/
          Library/
          ProjectSettings/
        build/
          osx/
            <prototype_name>.app/
              Contents/
                MacOS/
                   <prototype_name>
                ...
          win/
            <prototype_name>_Data
            <prototype_name>.exe
        doc/
      [<project-name>/]
        [package/]
          [<package_name>.unitypackage]
        [doc/]

### Дополнения

Названия файлов и директорий не должны содержать пробелов.

Исполняемый файл для MacOS должен иметь права на исполнение.
