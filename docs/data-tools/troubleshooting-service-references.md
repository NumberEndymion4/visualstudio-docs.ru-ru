---
title: Диагностика ссылок на службы
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c244489f21dec3783aed9d970b46805d204a1104
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshoot-service-references"></a>Устранение неполадок ссылок на службы

В этом разделе перечислены распространенные проблемы, которые могут возникнуть при работе с Windows Communication Foundation (WCF) или ссылки на службы данных WCF в Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Ошибка возврата данных из службы

При возвращении `DataSet` или `DataTable` из службы, можно получить исключение «был превышен максимальный размер квоты входящих сообщений». По умолчанию `MaxReceivedMessageSize` для некоторых привязок задано относительно небольшое значение позволяет снизить уязвимость для атак типа "отказ в обслуживании". Можно увеличить это значение, чтобы избежать возникновения исключения. Дополнительные сведения см. в разделе <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Чтобы исправить эту ошибку, сделайте следующее:

1.  В **обозревателе решений**, дважды щелкните файл app.config, чтобы открыть его.

2.  Найдите `MaxReceivedMessageSize` свойства и измените его на большее значение.

## <a name="cannot-find-a-service-in-my-solution"></a>Не удается найти службу в решении

При нажатии кнопки **Discover** кнопку в **добавить ссылку на службу** диалоговое окно, один или несколько проектов библиотеки службы WCF в решении не отображаются в списке служб. Это может произойти, если библиотека службы будет добавлен в решение, но еще не скомпилирована.

Чтобы исправить эту ошибку, сделайте следующее:

-   В **обозревателе решений**, щелкните правой кнопкой мыши проект библиотеки служб WCF и нажмите кнопку **сборки**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Ошибка доступа к службе удаленного рабочего стола

Когда пользователь открывает службы WCF, размещенных на веб сервере через удаленный рабочий стол и пользователь не имеет права администратора, используется проверка подлинности NTLM. Если пользователь не обладает правами администратора, пользователь может получить следующее сообщение об ошибке: «не разрешен для схемы проверки подлинности клиента «Анонимный» HTTP-запроса. От сервера получен заголовок проверки подлинности был «NTLM».»

Чтобы исправить эту ошибку, сделайте следующее:

1.  В проекте веб-сайта, откройте **свойства** страницы.

2.  На **параметры запуска** снимите **проверки подлинности NTLM** флажок.

    > [!NOTE]
    > Следует отключить проверку подлинности NTLM только для веб-сайтов, которые содержат исключительно службы WCF. Безопасность для служб WCF осуществляется с помощью конфигурации в файле web.config. Это делает ненужной проверку подлинности NTLM.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Уровень доступа для созданных классов не оказывает влияния

Установка **уровень для созданных классов доступа** в диалоговом окне **Настройка ссылок на службы** диалоговое окно **внутренний** или **Friend** может работать не всегда. Хотя этот параметр отображается в диалоговом окне, полученные классы поддержки создаются с уровнем доступа `Public`.

Это известное ограничение определенных типов, например сериализованным <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Ошибка отладки кода службы

При пошаговом выполнении кода для службы WCF из клиентского кода, может возникнуть ошибка, связанная с отсутствующими символами. Это может произойти, когда служба, которая входила в состав решения был перемещен или удален из решения.

При первом добавлении ссылки на службу WCF, который является частью текущего решения, явная зависимость построения добавляется между проектом службы и проектом клиента службы. Это гарантирует, что клиент всегда имеет доступ к обновленным двоичным файлам службы, что особенно важно для отладки сценариев, таких как шаг с заходом из клиентского кода в код службы.

Если проект службы удаляется из решения, эта явная зависимость построения становится недействительной. Visual Studio не может гарантировать что перестраивается проект службы при необходимости.

Чтобы устранить эту ошибку, необходимо вручную перестроить проект службы:

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  В **параметры** диалогового окна разверните **проекты и решения**, а затем выберите **Общие**.

3.  Убедитесь, что **Показывать дополнительные конфигурации построения** флажок установлен и нажмите кнопку **ОК**.

4.  Загрузите проект службы WCF.

5.  В **Configuration Manager** диалоговое окно, набор **активная конфигурация решения** для **отладки**. Дополнительные сведения см. в разделе [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).

6.  В **обозревателе решений**, выберите проект службы WCF.

7.  На **построения** меню, нажмите кнопку **Перестроить** перестроить проект службы WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Службы данных WCF не отображаются в браузере

При попытке просмотреть XML-представление данных в [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer может неправильно интерпретировать данные как RSS-канал. Убедитесь, что параметр, чтобы отобразить RSS-каналы, отключен.

Чтобы устранить эту ошибку, отключите RSS-каналы:

1.  В Internet Explorer на **средства** меню, нажмите кнопку **обозревателя**.

2.  На **содержимого** вкладке **веб-каналы** щелкните **параметры**.

3.  В **параметры каналов** снимите флажок **включить чтения веб-канала** флажок и нажмите кнопку **ОК**.

4.  Нажмите кнопку **ОК** закрыть **обозревателя** диалоговое окно.

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)