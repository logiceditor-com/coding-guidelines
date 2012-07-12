Это черновик файла с описанием рекомендаций по структуре новых проектов при их
создании.

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
