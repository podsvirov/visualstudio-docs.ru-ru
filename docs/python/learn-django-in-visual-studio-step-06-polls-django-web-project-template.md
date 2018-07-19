---
title: Руководство. Сведения о Django в Visual Studio (шаг 6)
description: Пошаговое руководство по основам Django в контексте проектов Visual Studio, в особенности о функциях шаблона веб-проекта опроса Django, например административная настройка.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ab725659207813bb88d505b1318a175e602c5ade
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750497"
---
# <a name="tutorial-step-6-use-the-polls-django-web-project-template"></a>Шаг 6 руководства. Использование шаблона "Веб-проект опроса Django"

**Предыдущий шаг. [Tutorial step 5: Authenticate users in Django](learn-django-in-visual-studio-step-05-django-authentication.md)** (Шаг 5 руководства. Проверка подлинности пользователей в Django)

Ознакомившись с шаблоном "Веб-проект Django" Visual Studio, вы теперь можете рассмотреть третий шаблон Django "Веб-проект опроса Django", который создается на базе того же кода и иллюстрирует работу с базой данных.

На этом шаге вы научитесь делать следующее.

> [!div class="checklist"]
> - Создание проекта на основе шаблона и инициализация базы данных (шаг 6–1)
> - Ознакомление с моделями данных (шаг 6–2)
> - Применение миграций (шаг 6–3)
> - Ознакомление с представлениями и шаблонами страниц, созданных с использованием шаблона проекта (шаг 6–4)
> - Создание настраиваемого административного интерфейса (шаг 6–5)

Проект, созданный с помощью этого шаблона, аналогичен проекту, который можно получить, следуя указаниям из руководства [по написанию первого приложения Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) в документации Django. Веб-приложение состоит из общедоступного сайта, на котором пользователи могут просматривать результаты опросов и голосовать в них, а также из настраиваемого административного интерфейса, в котором можно управлять опросами. В нем используется та же система проверки подлинности, что и в шаблоне "Веб-проект Django", и интенсивнее используется база данных путем реализации моделей Django, как описано в следующих разделах.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Шаг 6–1. Создание проекта и инициализация базы данных

1. В Visual Studio перейдите к **обозревателю решений**, щелкните правой кнопкой мыши решение LearningDjango, созданное ранее в рамках этого руководства, и выберите **Добавить** > **Новый проект**. (Если же вы хотите использовать новое решение, вместо этого выберите **Файл** > **Создать** > **Проект**.)

1. В диалоговом окне создания проекта найдите и выберите шаблон "Веб-проект опроса Django", вызовите проект "DjangoPolls" и нажмите кнопку **ОК**.

1. Как и другие шаблоны проектов в Visual Studio, шаблон "Веб-проект опроса Django" содержит файл `requirements.txt`, в котором Visual Studio запрашивает, куда установить эти зависимости. Выберите параметр **Install into a virtual environment** (Установка в виртуальном окружении) и в диалоговом окне **Добавление виртуального окружения** выберите **Создать**, чтобы принять значения по умолчанию.

1. После завершения настройки виртуального окружения в Python следуйте инструкциям в отображаемом файле `readme.html`, чтобы инициализировать базу данных и создать суперпользователя Django (т. е. администратора). Для этого сначала щелкните правой кнопкой мыши проект "DjangoPolls" в **обозревателе решений**, выберите **Python** >  команду **Миграция Django**, затем еще раз щелкните правой кнопкой мыши проект, выберите **Python** >  команду **Создание суперпользователя Django** и следуйте инструкциям. (При попытке сначала создать суперпользователя отобразится сообщение об ошибке, так как база данных не инициализирована.)

1. Для проекта "DjangoPolls" установите значение по умолчанию для решения Visual Studio, щелкнув правой кнопкой мыши этот проект в **обозревателе решений** и выбрав **Set as Startup Project** (Назначить запускаемым проектом). Запускаемый проект, выделенный полужирным шрифтом, выполняется при запуске отладчика.

1. Выберите **Отладка > Начать отладку** (F5) или нажмите кнопку **Веб-сервер** на панели инструментов, чтобы запустить сервер:

    ![Кнопка панели инструментов запуска веб-сервера в Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Приложение, созданное с помощью шаблона, содержит три страницы — домашнюю страницу, вкладки "О программе" и "Контактные сведения", перемещаться по которым можно с использованием верхней панели навигации. Выделите пару минут на просмотр различных частей приложения (страницы "О программе" и "Контактные сведения" очень похожи на страницу "Веб-проект Django" и не будут обсуждаться в дальнейшем).

    ![Полное представление приложения веб-проекта опроса Django в браузере](media/django/step06-full-app-view.png)

1. Кроме того, выберите ссылку **Администрирование** на панели навигации, где отображается экран входа. Это указывает на то, что административный интерфейс доступен только для администраторов, прошедших проверку подлинности. Воспользуйтесь учетными данными суперпользователя, после чего вы будете направлены на страницу "/admin", которая включена по умолчанию при использовании этого шаблона проекта.

    ![Административное представление приложения веб-проекта опроса Django](media/django/step06-polls-administrative-interface.png)

1. Вы можете оставить приложение запущенным и пройти следующие разделы.

    Чтобы остановить работу приложения и [зафиксировать изменения в системе управления исходным кодом](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), сначала откройте страницу **Изменения** в **Team Explorer**, щелкните правой кнопкой мыши папку виртуального окружения (возможно, `env`) и выберите **Игнорировать эти локальные элементы**.

### <a name="examine-the-project-contents"></a>Анализ содержимого проекта

Как было отмечено ранее, с большей частью содержимого проекта, созданного на основе шаблона "Веб-проект опроса Django", вы должны быть знакомы, если изучили другие шаблоны проектов Visual Studio. В дополнительных шагах этой статьи приведены более значительные изменения и дополнения, а именно модели данных и дополнительные представления.

### <a name="question-what-does-the-django-migrate-command-do"></a>Вопрос. Какое действие выполняет команда "Миграция Django"?

Ответ. Команда **Миграция Django** выполняет команду `manage.py migrate`, которая запускает все скрипты в папке `app/migrations`, которая еще не запускалась. В этом случае команда выполняет скрипт `0001_initial.py` в этой папке, чтобы настроить необходимую схему в базе данных.

Скрипт миграции создается с помощь команды `manage.py makemigrations`, которая проверяет файл `models.py` приложения, сравнивает его с текущим состоянием базы данных и создает необходимые скрипты для миграции схемы базы данных в соответствии с текущими моделями. Эта функция Django чрезвычайно полезная во время обновлений и изменений моделей со временем. Создавая и выполняя миграции, можно постоянно синхронизировать модели с базой данных, прилагая незначительные усилия.

Миграция выполняется на шаге 6–3 далее в этой статье.

## <a name="step-6-2-understand-data-models"></a>Шаг 6–2. Ознакомление с моделями данных

Модели с именем Poll and Choice для приложения определены в `app/models.py`. Каждая из них относится к классу Python, производному от `django.db.models.Model` и использующему методы класса `models`, такие как `CharField` и `IntegerField`, для определения полей в модели, сопоставляемых со столбцами базы данных.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Как видите, в Poll сохраняется описание в поле `text` и дата публикации в `pub_date`. Эти поля являются единственными, которые существуют для класса Poll в базе данных. Значение поля `total_votes` вычисляется во время выполнения.

Модель Choice связана с моделью Poll через поле `poll`, которое содержит описание в `text` и сохраняет количество для этого выбора в `votes`. Значение поля `votes_percentage` вычисляется во время выполнения и не содержится в базе данных.

Полный список типов полей — `CharField` (ограниченный текст) `TextField` (неограниченный текст), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` и `ManyToMany`. Каждое поле принимает некоторые атрибуты, такие как `max_length`. Атрибут `blank=True` означает, что поле необязательное. `null=true` означает, что значение необязательное. Кроме того, есть атрибут `choices`, который ограничивает значения только теми, что находятся в массиве кортежей значений данных, и теми, что отображаются в кортежах. (См. [ссылку на поле модели](https://docs.djangoproject.com/en/2.0/ref/models/fields/) в документации по Django.)

Вы можете проверить, что именно хранится в базе данных, просмотрев файл `db.sqlite3` в проекте с помощью таких средств, как [браузер SQLite](http://sqlitebrowser.org/). В базе данных поле внешнего ключа, такое как `poll`, в модели Choice хранится в виде `poll_id`. Django обрабатывает сопоставление автоматически.

Как правило, работа с базой данных в Django подразумевает работу исключительно с вашими моделями, чтобы программа Django могла управлять основной базой данных от вашего имени.

### <a name="seed-the-database-from-samplesjson"></a>Заполнение базы данных значениями из samples.json

Изначально база данных не содержит опросы. С помощью административного интерфейса можно добавить опросы вручную в URL-адрес "/admin", а также можно посетить страницу "/seed" на работающем сайте, чтобы заполнить базу данных опросами, определенными в файле `samples.json` приложения.

В файл `urls.py` проекта Django добавлен шаблон URL-адреса, `url(r'^seed$', app.views.seed, name='seed'),`. Представление `seed` в `app/views.py` загружает файл `samples.json` и создает необходимые модели объектов. Затем Django автоматически создает соответствующие записи в основной базе данных.

Обратите внимание на использование декоратора `@login_required` для указания уровня авторизации для представления.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Чтобы увидеть результат, сначала запустите приложение. Вы убедитесь, что опросов еще нет. Посетите URL-адрес "/seed", и когда приложение возвратится на домашнюю страницу, вы увидите, что опросы стали доступны. Опять же, вы можете изучить необработанный файл `db.sqlite3` с помощью такого средства, как [браузер SQLite](http://sqlitebrowser.org/).

![Приложение веб-проекта опроса Django с базой данных, заполненной начальными значениями](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Вопрос. Можно ли инициализировать базу данных с помощью административной служебной программы Django?

Ответ. Да, выполнить задачу, подобную заполнению страницы в приложении, можно с помощью [команды django-admin loaddata](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata). При работе с полным веб-приложением можно использовать сочетание двух методов: инициализировать базу данных из командной строки, а затем преобразовать страницу начальных значений в интерфейс API, в который можно отправлять любые произвольные объекты JSON, а не полагаться на жестко запрограммированный файл.

## <a name="step-6-3-use-migrations"></a>Шаг 6–3. Использование миграций

При запуске команды `manage.py makemigrations` (с помощью контекстного меню в Visual Studio) после создания проекта в Django создается файл `app/migrations/0001_initial.py`. Этот файл содержит скрипт, который создает таблицы исходной базы данных.

Так как со временем в модели постоянно вносятся изменения, Django позволяет легко поддерживать актуальность базовой схемы базы данных в отношении этих моделей. Общий рабочий процесс выглядит следующим образом:

1. Внесите изменения в модели в вашем файле `models.py`.
1. В Visual Studio щелкните правой кнопкой мыши проект в **обозревателе решений** и выберите **Python** команду  > **Django Make Migrations** (Выполнить миграцию Django). Как упоминалось ранее, эта команда создает скрипты в `app/migrations` для переноса базы данных из текущего состояния в новое.
1. Чтобы применить скрипты к фактической базе данных, щелкните правой кнопкой мыши проект и выберите **Python** > **Миграция Django**.

Django отслеживает, какие миграции были применены к любой конкретной базе данных. Таким образом, при выполнении команды миграции Django применяет необходимую миграцию. К примеру, если при создании новой пустой базы данных выполнить команду миграции, будут применены все скрипты миграции и база данных будет переведена в актуальное состояние, соответствующее текущим моделям. Аналогичным образом, если внести несколько изменений в модели и создать миграции на компьютере разработчика, можно применить накопительные миграции к рабочей базе данных, выполнив команду миграции на рабочем сервере. Django повторно применяет только те скрипты миграции, которые были созданы после последней миграции рабочей базы данных.

Чтобы увидеть эффект от изменения модели, сделайте следующее:

1. Добавьте необязательное поле author в `app/models.py` модели Poll, присоединив следующую строку после поля `pub_date`, чтобы получить необязательное поле `author`:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Сохраните файл, затем щелкните правой кнопкой мыши проект "DjangoPolls" в **обозревателе решений** и выберите **Python** команду  > **Django Make Migrations** (Выполнить миграцию Django).
1. Выберите **Проект** >  команду **Show All Files** (Показать все файлы), чтобы увидеть созданный скрипт в папке `migrations` с именем, начинающимся с `002_auto_`. Щелкните правой кнопкой мыши файл и выберите команду **Include In Project** (Включить в проект). Затем можно выбрать **Проект** > **Show All Files** (Показать все файлы) еще раз, чтобы восстановить исходное представление. (Подробные сведения об этом шаге см. во втором вопросе ниже.)
1. При необходимости откройте этот файл, чтобы проверить, как в Django создается скрипт изменения с предыдущего состояния модели на новое состояние.
1. Щелкните правой кнопкой мыши проект Visual Studio и выберите **Python** > **Миграция Django**, чтобы применить изменения к базе данных.
1. При желании откройте базу данных в соответствующем средстве просмотра, чтобы подтвердить изменение.

В целом благодаря функции миграции Django вам никогда не придется управлять схемой базы данных вручную. Просто внесите изменения в модели, создайте скрипты миграции и примените их с помощью команды миграции.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Вопрос. Что произойдет, если забыть выполнить команду миграции после внесения изменений в модели?

Ответ. Если модели не соответствуют содержимому базы данных, работа программы Django завершается ошибкой во время выполнения с соответствующими исключениями. Например, если вы забыли перенести изменение модели, описанное в предыдущем разделе, появится сообщение об ошибке "no such column: app_poll.author":

![Ошибка, отображающаяся, если не перенести изменение модели](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Вопрос. Почему в обозревателе решений после выполнения команды Django Make Migrations (Выполнить миграцию Django) не отображаются вновь созданные скрипты?

Ответ. Несмотря на то что вновь созданные скрипты находятся в папке `app/migrations` и применяются при выполнении команды **Миграция Django**, они не отображаются автоматически в **обозревателе решений** из-за того, что они не были добавлены в проект Visual Studio. Чтобы они отображались, сначала выберите **Проект** >  команду меню **Show All Files** (Показать все файлы) или кнопку панели инструментов, выделенную на рисунке ниже. Если выполнить эту команду, в **обозревателе решений** будут отображаться все файлы в папке проекта, при этом для элементов, которые не были добавлены в сам проект, будут использоваться значки с пунктирной линией. Щелкните правой кнопкой мыши файлы, которые требуется добавить, и выберите **Include In Project** (Включить в проект), в результате чего они также будут добавлены в систему управления исходным кодом со следующей фиксацией.

![Команда Include in Project (Включить в проект) в обозревателе решений](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Вопрос. Можно ли узнать, какие виды миграции будут применяться перед запуском команды миграции?

Ответ. Да, воспользуйтесь [командой django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Шаг 6–4. Ознакомление с представлениями и шаблонами страниц, созданных с использованием шаблона проекта

Большинство представлений, созданных с использованием шаблона "Веб-проект опроса Django", такие как представления для страниц "О программе" и "Контактные сведения", похожи на представления, созданные с использованием шаблона "Веб-проект Django", с которым вы работали ранее в этом руководстве. Отличительной чертой приложения Polls является то, что для домашней страницы используются модели, как и для нескольких добавленных страниц для голосования и просмотра результатов опроса.

Для начала первая строка в массиве `urlpatterns` в файле `urls.py` проекта Django — это нечто большее, чем просто перенаправление к представлению приложения. Вместо этого он получает файл `urls.py` приложения:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Файл `app/urls.py` содержит более интересный код маршрутизации (пояснительные комментарии добавлены):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Если вы не знакомы с более сложными регулярными выражениями, используемыми здесь, вы можете вставить выражение в [regex101.com](https://regex101.com/), чтобы получить объяснение простым языком. (Вам потребуется создать escape-символы для косых черт `/`, добавив обратную косую черту `\` перед ними. Это не является обязательным в Python из-за наличия префикса `r` в строке, означающего "raw".)

В Django синтаксис `?P<name>pattern` создает группу с именем `name`, которая передается как аргументы в представления в порядке их отображения. В коде, показанном выше, `PollsDetailView` и `PollsResultsView` получают аргумент с именем `pk` и `app.views.vote` принимает аргумент с именем `poll_id`.

Вы также можете видеть, что большая часть представлений — это не просто прямые ссылки на функцию представления в `app/views.py`. Вместо этого большинство из них ссылаются на класс в одном и том же файле, который является производным от `django.views.generic.ListView` или `django.views.generic.DetailView`. Базовые классы предоставляют методы `as_view`, которые принимают аргумент `template_name` для определения шаблона. Базовый класс `ListView`, который был использован для домашней страницы, также ожидает свойство `queryset`, содержащее данные, и свойство `context_object_name` с именем переменной, по которому необходимо ссылаться на данные в шаблоне, в этом случае `latest_poll_list`.

Теперь можно проверить домашнюю страницу в `PollListView`, что определено следующим образом в `app/views.py`:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Все это выполнено для определения модели, с которой работает представление (Poll), а также переопределяет метод `get_context_data`, чтобы добавить значения `title` и `year` в контекст.

Основа шаблона (`templates/app/index.html`) выглядит так:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Проще говоря, шаблон получает список объектов Poll в `latest_poll_list`, а затем выполняет итерацию этого списка, чтобы создать строку таблицы, содержащую ссылку на каждый опрос с помощью значения `text` опроса. В теге `{% url %}` "app:detail" указывает на шаблон URL-адреса в `app/urls.py` с именем "detail" с помощью `poll.id` в качестве аргумента. В результате этого Django создает URL-адрес с помощью соответствующего шаблона и использует его для ссылки. Такая технологическая перспективность означает, что этот шаблон URL-адреса можно изменить в любое время, а создаваемые ссылки автоматически обновляются для сопоставления.

Классы `PollDetailView` и `PollResultsView` в `app/views.py` (здесь не показаны) практически идентичны `PollListView`, за исключением того, что являются производным от `DetailView` вместо этого. Их соответствующие шаблоны, `app/templates/details.html` и `app/templates/results.html`, помещают соответствующие поля из моделей в различные элементы управления HTML. Отличительной чертой `details.html` является то, что варианты для опроса содержатся в форме HTML, которая при отправке выполняет запрос POST в URL-адрес /vote. Как показано выше, этот шаблон URL-адреса направляется в `app.views.vote`, который реализуется следующим образом (обратите внимание на аргумент `poll_id`, который снова представляет собой именованную группу в регулярном выражении, используемом в перенаправлении к этому представлению):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Здесь в представлении нет своего собственного соответствующего шаблона, как в других страницах. Вместо этого оно проверяет выбранный опрос, отображающий сообщение 404, если опрос не существует (на случай, если ввести URL-адрес в формате "vote/1a2b3c"). Затем оно проверяет, является ли выбранный вариант допустимым для опроса. Если нет, блок `except` просто отображает страницу сведений снова с сообщением об ошибке. Если вариант допустим, представление подсчитывает голоса и перенаправляет на страницу результатов.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Шаг 6–5. Создание настраиваемого административного интерфейса

Последняя часть шаблона "Веб-проект опроса Django" представляет собой пользовательские расширения для административного интерфейса Django по умолчанию, как показано выше в этой статье на шаге 6–1. По умолчанию интерфейс предоставляет возможности управления пользователями и группами и ничего более. Шаблон проекта Polls добавляет функции, которые позволяют также управлять опросами.

Во-первых, в шаблоны URL-адреса в `urls.py` проекта Django по умолчанию добавлен `url(r'^admin/', include(admin.site.urls)),`. Шаблон "admin/doc" также добавлен путем комментирования.

Приложение содержит файл `admin.py`, который Django автоматически запускает при посещении административного интерфейса благодаря добавлению `django.contrib.admin` в массив `INSTALLED_APPS` `settings.py`. Код в этом файле, как указано в шаблоне проекта, выглядит следующим образом:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Как видите, класс `PollAdmin` является производным от `django.contrib.admin.ModelAdmin` и настраивает количество полей с помощью имен из модели `Poll`, которой он управляет. Эти поля описаны в [параметрах ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) в документации по Django.

Если вызвать `admin.site.register`, класс подключится к модели (`Poll`) и добавит его в интерфейс администратора. Ниже приведен общий результат:

![Административное представление приложения веб-проекта опроса Django](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Следующие шаги

> [!Note]
> Если вы зафиксировали свое решение Visual Studio с системой управления исходным кодом в ходе работы с этим руководством, настало время сделать другую фиксацию. Ваше решение должно соответствовать исходному коду руководства на сайте GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Вы узнали все о шаблонах "Пустой веб-проект Django", "Веб-проект Django" и "Веб-проект опроса Django" в Visual Studio. Вы ознакомились с основами Django, а именно с использованием представлений и шаблонов, и изучили маршрутизацию, проверку подлинности и использование моделей базы данных. Теперь вы можете создать свое собственное веб-приложение с любыми необходимыми представлениями и моделями.

Запуск веб-приложения на компьютере разработчика — это лишь один шаг, чтобы сделать приложение доступным для клиентов. Следующие шаги могут включать приведенные ниже задачи:

- Настройка страницы 404 путем создания шаблона с именем `templates/404.html`. При наличии Django использует этот шаблон вместо шаблона по умолчанию. Дополнительные сведения см. в разделе о [представлениях ошибок](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) в документации по Django.

- Написание модульных тестов `tests.py`. Шаблоны проектов Visual Studio предоставляют отправные точки для них. Дополнительные сведения можно получить в статьях по [написанию первого приложения Django](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) и [тестированию Django](https://docs.djangoproject.com/en/2.0/topics/testing/) в документации по Django.

- Развертывание веб-приложения на рабочий сервер, например в службу приложений Azure. См. статью [Публикация в службу приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md), которая содержит сведения об определенных изменениях, необходимых для приложений Django.

- Изменение приложения с SQLite на хранилище данных промышленного уровня, например PostgreSQL, MySQL и SQL Server (все из них могут размещаться на платформе Azure). Как описано в статье про [использование SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite отлично работает с сайтами с низким и средним уровнем трафика с менее чем 100 тысяч попаданий/день, но использовать большие объемы не рекомендуется. Кроме того, он работает только на одном компьютере, поэтому может использоваться в любом сценарии с несколькими серверами, таком как балансировка нагрузки и георепликация. Сведения о поддержке Django в других базах данных см. в разделе [Database setup](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup) (Настройка базы данных). Вы можете также использовать [пакет SDK Azure для Python](azure-sdk-for-python.md), чтобы работать со службами хранилища Azure, такими как таблицы и большие двоичные объекты.

- Настройка конвейера непрерывной интеграции или непрерывного развертывания в таких службах, как Visual Studio Team Services (VSTS). В дополнение к работе с системой управления исходным кодом (в VSTS, GitHub или в другом месте), VSTS может автоматически выполнять модульные тесты в качестве необходимого условия для выпуска, а также настроить конвейер для развертывания на промежуточный сервер для дополнительных тестов перед развертыванием в рабочей среде. Кроме того, VSTS интегрируются с решениями мониторинга, такими как App Insights, и закрывают весь цикл средствами планирования Agile. Дополнительные сведения:

  - [Create a CI/CD pipeline for Python with the Azure DevOps Project](/vsts/build-release/apps/cd/azure/azure-devops-project-python?view=vsts) (Создание конвейера CI/CD для Python с помощью проекта Azure DevOps)
  - [Python development in Azure with Visual Studio Team Services](https://azure.microsoft.com/resources/videos/connect-2017-python-development-in-azure-with-visual-studio-team-services/) (Разработка Python в Azure с помощью Visual Studio Team Services).
