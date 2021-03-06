---
title: Запуск Windows Phone приложений в эмуляторе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683527"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Запуск приложений Windows Phone в эмуляторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эмулятор Windows Phone предоставляет виртуализированную среду, в которой можно производить отладку и тестирование приложений Windows Phone на компьютере, не имея физического устройства. Вы можете имитировать распространенные события касания и поворота и выбрать физический размер и разрешение экрана, которые требуется эмулировать. Вы также можете протестировать множество распространенных возможностей, таких как местоположение, работа в сети, уведомления, датчики, акселерометр и дополнительная SD-карта.  
  
 Дополнительные сведения о функциях, которые можно тестировать в эмуляторе, см. в разделе [Тестирование функций приложения в эмуляторе Windows Phone](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Вместе с Visual Studio эмулятор предоставляет готовую среду, в которой можно проектировать, разрабатывать, отлаживать и тестировать приложения Windows Phone.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Запуск приложения Windows Phone в эмуляторе  
 Во время разработки приложения Windows Phone вы можете использовать эмулятор Windows Phone для быстрого развертывания и тестирования приложения. Однако при этом рекомендуется перед публикацией в Магазине Windows Phone тестировать приложение на настоящем устройстве Windows Phone. Это позволяет вам взглянуть на свое приложение глазами пользователей.  
  
 При первом запуске приложения Windows Phone в эмуляторе Windows Phone возникает следующее событие:  
  
1. Запускается эмулятор.  
  
2. Эмулятор загружает операционную систему Windows Phone.  
  
3. Эмулятор отображает рабочий стол Windows Phone.  
  
4. Ваше приложение развертывается в эмуляторе.  
  
5. Ваше приложение запускается в эмуляторе.  
  
   Если выбранный эмулятор уже выполняется, ваше приложение развертывается и запускается в работающем эмуляторе. Одновременно может выполняться только один экземпляр каждого из эмуляторов.  
  
> [!TIP]
> При тестировании приложения в эмуляторе оставляйте эмулятор открытым между сеансами отладки, чтобы можно было быстро запустить приложение еще раз.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Запуск приложения из Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Развертывание и запуск приложения из Visual Studio  
  
1. В Visual Studio откройте проект Windows Phone.  
  
2. На **стандартной** панели инструментов выберите один из параметров эмулятора.  
  
     ![Список изображений эмулятора Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Чтобы развернуть и запустить приложение с помощью отладки, в меню **Отладка** выберите команду **начать отладку**или нажмите клавишу F5.  
  
     Чтобы развернуть и запустить приложение без отладки, в меню **Отладка** выберите команду **Запуск без отладки**или нажмите клавиши CTRL + F5.  
  
     Ваше приложение развертывается и запускается.  
  
     Чтобы развернуть приложение без его запуска, в меню **Сборка** выберите пункт **Развернуть решение**.  
  
##### <a name="to-stop-a-running-app"></a>Остановка выполняемого приложения  
  
- Чтобы остановить выполняемое приложение, выполните одно из следующих действий:  
  
  - В Visual Studio в меню **Отладка** выберите команду **прерывать отладку**или нажмите клавиши Shift + F5.  
  
  - В эмуляторе нажмите кнопку **назад** , чтобы выйти из приложения. Если активная страница приложения не была начальной страницей приложения, может потребоваться несколько раз нажать кнопку " **назад** ".  
  
    Работа приложения завершается, и отображается рабочий стол. При этом текущий сеанс отладки закрывается.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Перезапуск приложения без отладки  
  
1. На рабочем столе в эмуляторе проведите влево, чтобы открыть список приложений.  
  
2. В списке приложений коснитесь значка приложения. Приложение перезапускается без отладки.  
  
##### <a name="to-deactivate-a-running-app"></a>Отключение выполняемого приложения  
  
1. Перед запуском приложения в Visual Studio щелкните правой кнопкой мыши проект в обозреватель решений, а затем выберите пункт **Свойства** , чтобы открыть **Конструктор проектов**.  
  
2. В **конструкторе проектов**на странице **Отладка** снимите флажок захоронение при отключении **при отладке** , если требуется, чтобы приложение перейдет в неактивное состояние при отключении. Установите флажок, если хотите приложение полностью остановилось при отключении.  
  
3. В меню **Отладка** выберите команду **начать отладку**или нажмите клавишу F5, чтобы запустить приложение.  
  
4. В эмуляторе нажмите кнопку **Пуск** . Отображается рабочий стол, а приложение отключается. Приложение переходит в неактивное состояние или отдается захоронению в зависимости от установки флажка **захоронение при отладке** .  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Повторное включение неактивного или полностью отключенного приложения  
  
- В эмуляторе нажмите кнопку **назад** , чтобы вернуться к приложению. При переходе на другие страницы или открытии другого приложения может потребоваться несколько раз нажать кнопку " **назад** ", чтобы повторно активировать приложение.  
  
     Сеанс отладки возобновляется. Если отладчик был отсоединен от приложения, для возобновления сеанса отладки может потребоваться нажать клавишу F5.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Запуск приложения с помощью средства развертывания приложений  
 Для запуска приложения в эмуляторе можно также использовать средство Windows Phoneного развертывания приложений (**AppDeploy.exe**). Этот инструмент представляет собой автономное приложение и устанавливается при установке средств разработки Windows Phone.  
  
 Дополнительные сведения см. [в статье Развертывание приложений Windows Phone 8,1 с помощью средства развертывания приложений](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Настройка эмулятора Windows Phone с помощью панели инструментов эмулятора  
 В следующей таблице приведены кнопки конфигурации, доступные на панели инструментов эмулятора.  
  
|Кнопки на панели инструментов|Варианты настройки|  
|---------------------|---------------------------|  
|![Параметры ввода на панели инструментов эмулятора Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Настройка одноточечного и многоточечного ввода**<br /><br /> При включении многоточечного ввода вы можете щелкнуть правой кнопкой мыши, чтобы переместить точки касания, не касаясь экрана. После этого вы можете щелкнуть левой кнопкой мыши, чтобы переместить обе точки касания одновременно.|  
|![Ориентация на панели инструментов эмулятора Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Настройка ориентации эмулятора**<br /><br /> Вы можете изменить ориентацию эмулятора Windows Phone на одну из трех доступных: книжная, альбомная слева или альбомная справа. При смене ориентации размер эмулятора не изменяется.<br /><br /> Чтобы изменить ориентацию, нажмите кнопку **повернуть влево** или кнопку **повернуть вправо** .|  
|![Параметры размера на панели инструментов эмулятора Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Настройка размера эмулятора**<br /><br /> Вы можете изменить размер эмулятора на экране главного компьютера. Размер в точках на дюйм (DPI) у эмулятора определяется по разрешению монитора и не зависит от значения масштаба.<br /><br /> — Чтобы вписать эмулятор на экран, нажмите кнопку по **размеру экрана** .<br />— Чтобы изменить параметр масштаба, нажмите кнопку **масштаб** . Откроется диалоговое окно " **масштаб** ". В диалоговом окне **масштаб** введите значение масштаба от 33 до 100.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Использование имитации аппаратных кнопок в эмуляторе  
 Имитируйте использование кнопок телефона, используя имитацию кнопок на экране эмулятора.  
  
- Нажмите кнопку **питания** , чтобы имитировать включение и отключение экрана. Щелкните и удерживайте, чтобы имитировать выключение телефона.  
  
- Нажмите кнопку **вверх** или " **Громкость** ", чтобы имитировать изменение громкости динамика телефона для телефонных звонков и уведомлений.  
  
- Кнопка **Камера** запускает приложение камеры. Вы можете имитировать фото- или видеосъемку, используя элементы управления в приложении камеры.  
  
  На следующем снимке экрана приведены имитируемые кнопки.  
  
1. На левом изображении показан рабочий стол эмулятора.  
  
2. В среднем изображении эмулятор отображается после нажатия кнопки **питания** для выключения экрана.  
  
3. На правильном изображении отображается экран эмулятора после нажатия кнопки **Громкость** , чтобы увеличить том.  
  
   ![Кнопки на эмуляторе Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Использование компьютерной клавиатуры с эмулятором  
 Эмулятор поддерживает сопоставление аппаратной клавиатуры на компьютере разработчика с клавиатурой на Windows Phone. Функции кнопок аналогичны устройству Windows Phone.  
  
 По умолчанию аппаратная клавиатура выключена. Такая реализация аналогична сдвигающейся клавиатуре, которую необходимо развертывать перед использованием. До включения аппаратной клавиатуры эмулятор принимает ввод только с кнопок управления.  
  
 Специальные символы на клавиатуре локализованной версии компьютера разработчика Windows эмулятор не поддерживает. Чтобы ввести специальные символы, присутствующие на локализованной клавиатуре, используйте экранную панель ввода.  
  
 Чтобы использовать в эмуляторе клавиатуру компьютера, нажмите клавишу PAGE UP или PAUSE/BREAK (эмулятор Windows 8 и 8.1) или клавишу F4 (эмулятор Windows 10).  
  
 Чтобы отключить клавиатуру компьютера в эмуляторе, нажмите клавишу PAGE UP или PAUSE/BREAK (эмулятор Windows 8 и 8.1) или клавишу F4 (эмулятор Windows 10).  
  
 В следующей таблице приведены клавиши на аппаратной клавиатуре, которые можно использовать для эмуляции кнопок и других элементов управления на Windows Phone.  
  
|Клавиша на компьютере|Кнопка Windows Phone|Примечания|  
|---------------------------|-----------------------------------|-----------|  
|F1|ВОЗВРАТ|Длинные нажатия работают согласно ожиданиям.|  
|F2|START|Длинные нажатия работают согласно ожиданиям.|  
|F3|SEARCH||  
|F4|В эмуляторе Windows 10 переключение между включением и отключением использования клавиатуры локального компьютера.|Неприменимо в эмуляторе Windows 8 и 8.1.|  
|F5|Неприменимо.||  
|F6|КАМЕРА, НЕПОЛНОЕ НАЖАТИЕ|Выделенная кнопка камеры, нажимаемая до середины.|  
|F7|КАМЕРА, ПОЛНОЕ НАЖАТИЕ|Выделенная кнопка камеры.|  
|F8|Неприменимо.||  
|F9|УВЕЛИЧЕНИЕ ГРОМКОСТИ||  
|F10|УМЕНЬШЕНИЕ ГРОМКОСТИ||  
|F11|Неприменимо.||  
|F12|POWER|Нажмите клавишу F12 дважды, чтобы включить экран блокировки.<br /><br /> Длинные нажатия работают согласно ожиданиям.|  
|ESC|ВОЗВРАТ|Длинные нажатия работают согласно ожиданиям.|  
|PAUSE/BREAK|Переключение клавиатуры (только в эмуляторе Windows 8 и 8.1).|Неприменимо в эмуляторе Windows 10.|  
|PAGE UP|Включает аппаратную клавиатуру (только в эмуляторе Windows 8 и 8.1).|Неприменимо в эмуляторе Windows 10.|  
|PAGE DOWN|Выключает аппаратную клавиатуру (только в эмуляторе Windows 8 и 8.1).|Неприменимо в эмуляторе Windows 10.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Сохранение и Загрузка пользовательских контрольных точек  
 Сохраните моментальный снимок состояния эмулятора с помощью вкладки **контрольные точки** в **дополнительных средствах**эмулятора. Эта возможность полезна, если вы часто тестируете приложение с одними и теми же параметрами и данными.  
  
 Например, если вашему приложению требуется несколько контактов, вы можете создать их один раз, а затем сохранить моментальный снимок эмулятора. В противном случае вам потребуется создавать эти контакты при каждом запуске эмулятора.  
  
- Щелкните **создать контрольную точку** , чтобы записать новый моментальный снимок состояния эмулятора с данными и параметрами, необходимыми для повторного тестирования приложения. Новая контрольная точка добавляется в список **контрольных точек** .  
  
   Вы не можете получить создать контрольную точку, пока к эмулятору подсоединен отладчик.  
  
- Выберите контрольную точку в списке **контрольные точки** , чтобы просмотреть сведения о контрольной точке.  
  
- Выберите переключатель в столбце **по умолчанию** , чтобы сделать сохраненную контрольную точку контрольной точкой по умолчанию для активного эмулятора.  
  
- Нажмите кнопку **восстановить** , чтобы перезапустить операционную систему Windows Phone в эмуляторе и загрузить выбранный моментальный снимок.  
  
- Нажмите кнопку **Удалить** , чтобы удалить моментальный снимок, который больше не нужен.  
  
  Исходный образ эмулятора всегда отображается как первый элемент в списке **контрольных точек** и не может быть изменен или удален. Однако вы можете выбрать другой снимок в качестве образа эмулятора по умолчанию.  
  
  ![Вкладка "Контрольные точки" эмулятора Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Запись снимков экрана в эмуляторе  
 Вы можете создавать снимки экрана для своих приложений Windows Phone, используя соответствующий инструмент в окне "Дополнительные средства". Инструмент создает файлы PNG, которые по разрешению соответствуют запущенному эмулятору.  
  
 ![Снимки экрана из эмулятора Windows Phone](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Создание снимка экрана приложения с помощью встроенного в эмулятор инструмента  
  
1. Чтобы добиться оптимального качества снимков экрана, установите уровень масштаба эмулятора на 100 процентов. Чем выше уровень масштабирования, тем лучше качество снимка экрана.  
  
2. Запустите свое приложение в эмуляторе.  
  
3. На панели инструментов эмулятора нажмите кнопку развернуть, чтобы открыть окно **дополнительные средства** .  
  
4. Перейдите на вкладку **снимок экрана** .  
  
5. Когда приложение будет готово, нажмите кнопку **Capture (захватить** ).  
  
    Снимок экрана отображается в рабочей области.  
  
6. Нажмите кнопку " **сохранить** ", чтобы открыть диалоговое окно " **Сохранить как** ".  
  
7. Выберите нужное расположение и **имя файла** и нажмите кнопку **сохранить**.  
  
8. Можно также перейти на другие страницы в приложении и создать дополнительные снимки экрана.  
  
9. Запустите эмулятор с другим разрешением экрана, чтобы создать такие же снимки с другим разрешением. Если вы запустили приложение с отладкой, потребуется остановить отладку, прежде чем повторно запустить ее в другом эмуляторе.  
  
   Отключите счетчики частоты кадров на экране эмулятора, прежде чем делать снимки экрана, которые будут отправлены в Магазин Windows Phone.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Отключение счетчиков частоты кадров в эмуляторе перед получением снимков экрана  
  
- Укажите сборку выпуска в Visual Studio. После указания сборки выпуска запустите приложение, выбрав ссылку **Развернуть _[имя приложения]_ ** в меню **Сборка** .  
  
- Кроме того, вы можете закомментировать строку кода в файле app.xaml.cs или app.xaml.vb, где для `EnableFrameRateCounter` устанавливается значение `true`.
