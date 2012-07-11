Это черновик файла с описанием рекомендаций по структуре новых проектов при их
создании.

## Прототип на движке Unity 3D

    <git-repo-name>/
      prototype/
        app/
          Assets/
          Library/
          ProjectSettings/
        build/
          osx/
            <prototype_name>.app/
              Contents/
                MacOS/
                  <executable_name>
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

Имя файла `<executable_name>` не должно содержать пробелов, а сам файл должен
иметь права на исполнение.
