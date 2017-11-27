---
title: "Захват графической информации | Документы Microsoft"
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: "41"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68e02e99eb621a5f7884e9848f0065fa0220be92
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="capturing-graphics-information"></a>Захват графической информации
Захватывайте информацию графики из приложений DirectX, чтобы можно было использовать анализатор графики Visual Studio для диагностики проблем отрисовки и проблем производительности.  
  
## <a name="capturing-graphics-information"></a>Захват графической информации  
 Захват графической информации представляет собой двухэтапный процесс. На первом этапе приложение запускается в режиме диагностики графики и указываются один или более кадров для захвата подробной графической информации.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Запуск приложения в режиме диагностики графики  
  
-   В строке меню выберите **отладки**, **графики**, **начать отладку графики**. (Сочетание клавиш: Alt+F5)  
  
-   На **графики** инструментов, выберите **начать отладку графики** кнопки.  
  
 Во время выполнения приложения в режиме диагностики графики постоянно записывается определенная графическая информация; она включает настройку устройства, создания цепочки буферов, создание графических объектов и ресурсов и другие важные события, влияющие более чем на один кадр. В то же время можно записать подробные сведения об определенных кадрах; к ним относятся вызовы рисования и операции вычислительного шейдера, а также объекты Direct3D и поддерживающие их ресурсы.  
  
### <a name="to-capture-a-frame"></a>Захват кадра  
  
-   В Visual Studio на **графики** инструментов, нажмите кнопку **захват кадра** кнопку ![значок кнопки захвата графики](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   На клавиатуре нажмите клавишу Print Screen.
  
    > [!NOTE]
    >  Пока приложение выполняется под **диагностики графики**, клавишу Print Screen можно использовать только для захвата кадра графических данных; она не выполняет свою обычную функцию. Это продолжается до завершения захвата графической информации (как правило, в результате остановки отладки или выхода из приложения обычным образом), даже если в фокусе находится другое приложение.  
  
-   В интерфейсе захвата Visual Studio, выберите **захват кадра** расположенную ниже **диагностического сеанса** временной шкалы, или нажмите большую **захват кадра** кнопки он располагается ниже **кадров в секунду** под дорожкой справа от каких-либо ранее захваченных кадров. Обе кнопки выделены на рисунке ниже.  
  
     ![Захват кадров с помощью средства использования GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
     Когда вы будете готовы для проверки кадров, захваченных, запустите **анализатор графики Visual Studio** , следуя **кадров...**  ссылку над эскизами или дважды щелкнув эскиз.  
  
 Могут захватываться только целые кадры, поэтому при запуске захвата фактически графические данные из следующего кадра, которое записывается. Запись начинается сразу после вывода кадра, на котором был запущен захват, и заканчивается после вывода захваченного кадра. Во время работы приложения в режиме диагностики графики можно захватить любое количество кадров. Если никакие кадры не захватываются, журнал графики очищается.  
  
 Во время записи кадров Visual Studio отображает окно диагностики сеанса (.diagsession). Если закрыть это окно, остановить отладку или закрыть приложение, не удается записать в этот журнал новые кадры. Чтобы получить больше информации графики, необходимо снова запустить приложение в режиме диагностики графики, чтобы начать новый журнал графики.  
  
### <a name="graphics-diagnostics-capture-options"></a>Параметры захвата диагностики графики  
 Вы можете настроить функцию захвата так, чтобы собирались стеки вызовов для всех событий графики или только для ограниченного их подмножества, отключить HUD захвата и включить или отключить режим совместимости захвата.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Настройка параметров захвата диагностики графики  
  
1.  В строке меню в меню "Сервис" выберите пункт "Параметры". Откроется диалоговое окно "Параметры".  
  
2.  В списке категорий параметров слева выберите пункт «Диагностика графики», а затем настройте необходимые параметры диагностики графики.  
  
     **Сбор стеков вызовов во время захвата (замедляет захват)**  
     Чтобы осуществлять сбор стеков вызовов, установите этот флажок. По умолчанию стеки вызовов не собираются. Чтобы захватывать стеки вызовов, убедитесь, что **звонок стеков во время захвата (захват замедляется** флажок устанавливается для включения коллекции и затем установите либо **draw, dispatch, present и производительности маркеров**параметра (по умолчанию), чтобы собирать только наиболее важные стеки вызовов, или **для всего** параметр, чтобы собирать все стеки вызовов. Чтобы прекратить сбор стеков вызовов позднее, снимите **звонок стеков во время захвата (захват замедляется** флажок.  
  
     **Отключить HUD в игре во время захвата**  
     Установите этот флажок, чтобы отключить наложение HUD, которое обычно отображается в приложении, находящемся в режиме диагностики графики. Чтобы отображать наложение HUD, снимите этот флажок.  
  
     **Выполнить захват в режиме совместимости**  
     Установите этот флажок, чтобы захватывать графические данные в режиме совместимости. По умолчанию захват выполняется в режиме совместимости. В режиме совместимости Direct3D не будет сообщать о том, что GPU поддерживает дополнительные функции помимо тех, которые определены на базовом функциональном уровне. Это позволяет предотвратить использование в приложении, в котором выполняется захват, специфичных для оборудования расширений GPU и обеспечивает возможность воспроизведения журнала графики с помощью любого GPU, поддерживающего тот же или более высокий функциональный уровень. Чтобы отключить режим совместимости, снимите этот флажок. Журналы, захваченные при отключенном режиме совместимости, не удастся воспроизвести на GPU, который не поддерживает дополнительные возможности, использовавшиеся приложением во время захвата.  
  
     **Остановить запись, если найдены ошибки уровней пакета SDK**  
     Установите этот флажок, чтобы немедленно останавливать запись при возникновении ошибок.  
  
## <a name="capturing-graphics-information-remotely"></a>Удаленный захват графической информации  
 Графическую информацию можно захватывать из приложения, работающего на локальном компьютере или на удаленном компьютере или устройстве. Удаленный захват поддерживается для компьютеров с [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] и устройств [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Чтобы захватить графическую информацию из приложения, выполняющегося удаленно, настройте проект для удаленной отладки, а затем запустите приложение в режиме диагностики графики, как было описано выше. Приложение будет выполняться на удаленном компьютере, а захваченная графическая информация будет собираться на компьютере разработки.  
  
 Настройка проекта для удаленной отладки зависит от типа разрабатываемого приложения и используемого языка программирования. Сведения о настройке удаленной отладки для приложений UWP в разделе [приложений UWP, запустите на удаленном компьютере](../run-windows-store-apps-on-a-remote-machine.md). Сведения о настройке удаленной отладки для приложения рабочего стола Windows, см. в разделе [удаленной отладки](../remote-debugging.md).  
  
 Впоследствии удаленный компьютер или устройство можно использовать для воспроизведения графической информации независимо от того, где она была захвачена. Дополнительные сведения см. в разделе [как: изменение машины воспроизведения диагностики графики](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Захват графических данных из командной строки  
 С помощью программы командной строки можно захватывать графические данные из любых приложений. Программа DXCap.exe позволяет быстро захватывать и воспроизводить графические данные без использования Visual Studio или программного захвата. В частности, программу DXCap.exe можно использовать для автоматизации или в тестовой среде. Дополнительные сведения о DXCap.exe см. в разделе [командной строки для захвата](command-line-capture-tool.md)  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Запись сведений графики](walkthrough-capturing-graphics-information.md)