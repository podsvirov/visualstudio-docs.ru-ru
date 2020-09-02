---
title: Руководство по DOCKER. Начало работы с DOCKER
description: Многошаговый учебник, посвященный основам работы с DOCKER с Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176841"
---
# <a name="tutorial-get-started-with-docker"></a>Учебник. Начало работы с DOCKER

В этом руководстве вы узнаете о создании и развертывании приложений DOCKER, включая использование нескольких контейнеров с базой данных и использование Docker Compose. Вы также развернете контейнерное приложение в Azure.

## <a name="start-the-tutorial"></a>Начать изучение руководства

Если вы уже выпустили команду, чтобы приступить к работе с руководством, Поздравляем!  В противном случае откройте командную строку или окно Bash и выполните следующую команду:

```cli
docker run -d -p 80:80 docker/getting-started
```

Обратите внимание на несколько используемых флагов. Ниже приведены некоторые дополнительные сведения.

- `-d` — Запуск контейнера в отключенном режиме (в фоновом окне)
- `-p 80:80` — Сопоставьте порт 80 узла с портом 80 в контейнере.
- `docker/getting-started` — используемый образ;

> [!TIP]
> Для сокращения полной команды можно использовать однозначные флаги.
> Например, приведенная выше команда может быть написана следующим образом:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Расширение VS Code

Прежде чем приступить к работе, необходимо выделить расширение DOCKER VS Code, которое позволяет быстро просмотреть контейнеры, работающие на вашем компьютере. Он обеспечивает быстрый доступ к журналам контейнеров, позволяет получить оболочку внутри контейнера и позволяет легко управлять жизненным циклом контейнера ("прекратить", "Удалить" и т. д.).

Чтобы получить доступ к расширению, следуйте приведенным [здесь](https://code.visualstudio.com/docs/containers/overview)инструкциям. Используйте значок DOCKER слева, чтобы открыть представление DOCKER. Если открыть расширение сейчас, вы увидите, что это руководство работает. Имя контейнера ( `angry_taussig` ниже) является именем, созданным случайным образом. Поэтому у вас скорее всего будет другое имя.

![Контейнер Tutorial, выполняемый в расширении DOCKER](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Что такое контейнер

Теперь, когда вы запустили контейнер, что *представляет* собой контейнер? Проще говоря, контейнер — это просто другой процесс на компьютере, который был изолирован от всех других процессов на хост-компьютере. Такая изоляция использует [пространства имен ядра и cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), функции, которые были в Linux в течение длительного времени. DOCKER работал над тем, чтобы сделать эти возможности удобными и простыми в использовании.

> [!NOTE]
> **Создание контейнеров с нуля** Если вы хотите увидеть, как создаются контейнеры с нуля, основными Райс от голубого по безопасности имеет видео, в котором она создает контейнер с нуля в Go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Что такое образ контейнера

При запуске контейнера используется изолированная файловая система. Эта пользовательская файловая система предоставляется **образом контейнера**. Поскольку образ содержит файловую систему контейнера, он должен содержать все необходимое для запуска приложения — все зависимости, конфигурацию, скрипты, двоичные файлы и т. д. Образ также содержит другую конфигурацию для контейнера, например переменные среды, выполняемую командой по умолчанию и другие метаданные.

В дальнейшем мы подробно рассмотрим образы, охватывающие такие темы, как слои, рекомендации и многое другое.

> [!NOTE]
> Если вы знакомы с, вы можете `chroot` рассматривать контейнер как расширенную версию `chroot` . Файловая система просто поступает из образа. Однако контейнер добавляет дополнительную изоляцию недоступен при простом использовании чрут.

## <a name="next-steps"></a>Дальнейшие действия

Продолжайте работу с руководством.

> [!div class="nextstepaction"]
> [Приложение](your-application.md)