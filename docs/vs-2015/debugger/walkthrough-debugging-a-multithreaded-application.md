---
title: Пошаговое руководство. Отладка многопоточного приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683085"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Пошаговое руководство. Отладка многопоточных приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] предоставляет улучшенное окно **потоков** и другие улучшения пользовательского интерфейса, упрощающие отладку многопоточных приложений. Выполнение данного пошагового руководства занимает лишь несколько минут, но оно позволит ознакомиться с новыми возможностями интерфейса для отладки многопоточных приложений.  
  
 Чтобы начать работу с данным пошаговым руководством, необходим проект многопоточного приложения. Выполните следующие действия для создания этого проекта.  
  
#### <a name="to-create-the-walkthrough-project"></a>Чтобы создать проект для пошагового руководства  
  
1. В меню **файл** выберите пункт **создать** , а затем выберите пункт **проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2. В поле **тип проекта**выберите нужный язык: **Visual Basic**, **Visual C#** или **Visual C++**.  
  
3. В поле **шаблоны** выберите **консольное приложение** или **консольное приложение CLR**.  
  
4. В поле **имя** введите имя мисреадвалксраугхапп.  
  
5. Нажмите кнопку **ОК**.  
  
     Появится новый проект консольного приложения. Когда проект будет создан, откроется файл исходного кода. В зависимости от выбранного языка файл исходного кода может называться Module1.vb, Program.cs или MyThreadWalkthroughApp.cpp  
  
6. Удалите код, который отображается в исходном файле, и замените его примером кода, который отображается в разделе "Создание потока" раздела [Создание потоков и передача данных во время начала](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. В меню **Файл** выберите команду **Сохранить все**.  
  
#### <a name="to-begin-the-walkthrough"></a>Чтобы начать работу над пошаговым руководством  
  
- В окне исходного кода найдите следующий код:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Начало отладки  
  
1. Щелкните правой кнопкой мыши `Console.WriteLine` инструкцию, укажите пункт **точка останова** и выберите пункт **Вставить точку останова**.  
  
     В левом переплете окна исходного кода появится красный шар. Это означает, что точка останова установлена в этом месте.  
  
2. В меню **Отладка** выберите команду **Начать отладку**.  
  
     Начнется отладка, консольное приложение запустится и прервется на точке останова.  
  
3. Если в этот момент фокус находится на окне консольного приложения, щелкните окно [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для возвращения фокуса в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. В окне исходного кода найдите строку, содержащую следующий код:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>Чтобы обнаружить маркер потока  
  
1. Щелкните правой кнопкой мыши в окне **потоки** и выберите команду **отобразить потоки в исходном**виде.  
  
2. Посмотрите на переплет в левой части окна. На этой строке появится значок, похожий на 2 тряпичных нити. Одна нить красного цвета, другая — синего. маркер потока указывает, что некий поток остановлен в этом месте. Возможно, в данном месте остановлен наш поток.  
  
3. Наведите указатель мыши на маркер потока. Появится всплывающая подсказка. Подсказка сообщает имя и идентификационный номер каждого остановившегося тут потока. В нашем случае существует только один поток, имя которого, вероятно, `<noname>`.  
  
4. Щелкните правой кнопкой мыши маркер потока. Обратите внимание на варианты выбора в контекстном меню.  
  
   Этот значок является *маркером потока*:  
  
   ![Маркер потока](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Пометка потоков и ее снятие  
 В [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] можно пометить поток, которому следует уделить особое внимание. Пометка потоков — хороший способ отслеживать более важные потоки и игнорировать менее важные.  
  
#### <a name="to-flag-threads"></a>Чтобы пометить потоки  
  
1. В меню **вид** выберите пункт **панели инструментов**.  
  
     Убедитесь, что выбрана панель инструментов **место отладки** .  
  
2. Перейдите на панель инструментов **место отладки** и щелкните список **потоков** .  
  
    > [!NOTE]
    > Эту панель инструментов можно распознать тремя наглядными списками: **процесс**, **поток**и **кадр стека**.  
  
3. Обратите внимание, сколько потоков отображается в списке.  
  
4. Вернитесь в окно исходного кода и снова щелкните маркер **потока** правой кнопкой мыши.  
  
5. В контекстном меню выберите пункт **флаг**, а затем щелкните имя и идентификатор потока.  
  
6. Вернитесь на панель инструментов **Расположение отладки** и снова щелкните список **потоков** .  
  
     Теперь в списке отображаются только отмеченные потоки. Кнопка флага, расположенная непосредственно справа от списка **потоков** . Значок флага на кнопке ранее был тусклым. Теперь у него ярко–красная окраска.  
  
7. Наведите указатель мыши на значок флага.  
  
     Появится всплывающее окно. Это всплывающее окно содержит сведения о том, в каком режиме находится список **потоков** : **Показывать только отмеченные потоки**.  
  
8. Нажмите кнопку флаг, чтобы вернуться в режим **Показать все потоки** .  
  
9. Снова щелкните список **потоков** и убедитесь, что теперь все потоки снова отображаются.  
  
10. Нажмите кнопку флага, чтобы вернуться в режим **Показать только отмеченные потоки**.  
  
11. В меню **Отладка** выберите пункт **Окна** и затем щелкните **Потоки**.  
  
     Откроется окно **потоки** . К одному потоку прикреплен заметный значок флага.  
  
12. В окне исходного кода щелкните правой кнопкой мыши маркер потока еще раз.  
  
     Обратите внимание, какие варианты сейчас доступны в контекстном меню. Вместо **флага**теперь вы видите флажок снять **пометку**. Не нажимайте кнопку **снять пометку**.  
  
13. Перейдите к следующему шагу — как снять отметку с потока.  
  
#### <a name="to-unflag-threads"></a>Чтобы снять отметку с потока  
  
1. В окне **потоки** щелкните правой кнопкой мыши строку, соответствующую помеченному обсуждению.  
  
     Появится контекстное меню. Он имеет параметры для **снятия флагов** и **снятия отметки со всех**.  
  
2. Чтобы снять пометку для потока, нажмите **снять пометку**.  
  
3. Щелкните значок красного флажка.  
  
4. Снова взгляните на панель инструментов **место отладки** . Кнопка флага снова стала тусклой. Вы сняли отметку с только что отмеченного потока. Так как нет помеченных потоков, панель инструментов перешла в режим **отображения всех потоков** . Щелкните список **потоков** и убедитесь, что вы видите все потоки.  
  
5. Вернитесь в окно **потоки** и изучите информационные столбцы.  
  
     В верхней части каждой колонки большая часть кнопок имеет заголовки, которые идентифицируют колонку. Однако первый столбец слева не имеет заголовка. Вместо этого он имеет значок, являющийся контуром флага. Можно заметить тот же контур в каждой строке списка потоков. Контур означает, что поток не отмечен.  
  
6. Щелкните контуры флагов у двух потоков, второго и третьего снизу в списке.  
  
     Вместо контуров будут отображаться значки красных флагов.  
  
7. Нажмите кнопку в заголовке колонки флагов.  
  
     Порядок в списке потоков изменился, когда была нажата кнопка. Список потоков теперь отсортирован так, что отмеченные потоки располагаются в верху списка.  
  
8. Снова нажмите кнопку в заголовке колонки флагов.  
  
     Порядок сортировки изменился еще раз.  
  
## <a name="more-about-the-threads-window"></a>Дополнительные сведения об окне "Потоки"  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Чтобы получить дополнительные сведения об окне "Потоки"  
  
1. В окне **потоки** просмотрите третий столбец слева. На кнопке в верхней части этого столбца будет указано **идентификатор**.  
  
2. Щелкните **идентификатор**.  
  
     Теперь список потоков отсортирован по идентификатору потока.  
  
3. Щелкните правой кнопкой мыши любой поток в списке. В контекстном меню выберите пункт **шестнадцатеричное отображение**.  
  
     Формат идентификаторов потоков изменился.  
  
4. Наведите указатель мыши на любой поток в списке.  
  
     После небольшой задержки появится Подсказка Данных. Она отображает частичный стек вызова для этого потока.  
  
5. Взгляните на четвертый столбец слева, который помечен как **Категория**. Потоки делятся на категории.  
  
     Первый поток, созданный в процессе, называется "основной поток". Найдите его в списке потоков.  
  
6. Щелкните правой кнопкой мыши основной поток и выберите команду **переключиться на поток**.  
  
     Появится диалоговое окно с предупреждением. Оно сообщает, что [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не может отобразить исходный код для основного потока.  
  
     Нажмите кнопку **ОК**.  
  
7. Взгляните на окно **Стек вызовов** и панель инструментов **место отладки** .  
  
     Содержимое окна **стека вызовов** изменилось.  
  
## <a name="switching-the-active-thread"></a>Переключение активного потока  
  
#### <a name="to-switch-threads"></a>Чтобы переключаться между потоками  
  
1. В окне **потоки** просмотрите второй столбец слева. Кнопка в верхней части этого столбца не содержит текста или значка. Этот столбец является активным столбцом **потока** .  
  
2. Взгляните на столбец **Активный поток** и обратите внимание, что у одного потока есть желтая стрелка. Это *индикатор активного потока*.  
  
3. Запишите идентификатор потока, на котором установлен индикатор активного потока. Индикатор активного потока будет перемещен на другой поток, но после завершения его необходимо будет вернуть.  
  
4. Щелкните правой кнопкой мыши другой поток и выберите команду **переключиться на поток**.  
  
5. Взгляните на окно **Стек вызовов** в окне исходного кода. Его содержимое изменилось.  
  
6. Взгляните на панель инструментов **место отладки** . Здесь активный поток тоже был изменен.  
  
7. Перейдите на панель инструментов **место отладки** . Щелкните поле **поток** и выберите другой поток из раскрывающегося списка.  
  
8. Взгляните на окно **потоки** . Здесь изменился индикатор активного потока.  
  
9. В окне исходного кода щелкните правой кнопкой мыши маркер потока. В контекстном меню выберите пункт **Перейти к** и щелкните имя или идентификатор потока.  
  
     Теперь вы видели три способа изменения активного потока: с помощью окна **потоки** , поля **поток** на панели инструментов **место отладки** и индикатор потока в окне исходного кода.  
  
     С помощью индикатора потока можно переключаться только на потоки, остановленные в этом конкретном расположении. С помощью окна **Потоки** и панели инструментов **Место отладки** можно переключиться на любой поток.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Замораживание и размораживание потоков  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Чтобы заморозить и разморозить потоки  
  
1. В окне **потоки** щелкните правой кнопкой мыши любой поток и выберите команду **заморозить**.  
  
2. Посмотрите на столбец "Активный поток". В нем появилась пара вертикальных полос. Эти две синие полосы указывают, что поток заморожен.  
  
3. Взгляните на столбец **Suspend** . Счетчик приостановки для потока теперь имеет значение 1.  
  
4. Щелкните правой кнопкой мыши замороженный поток и выберите команду **разморозить**.  
  
     Столбец "активный поток" и изменение столбца **приостановки** .  
  
## <a name="see-also"></a>См. также:  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Как переключиться на другой поток во время отладки](../debugger/how-to-switch-to-another-thread-while-debugging.md)
