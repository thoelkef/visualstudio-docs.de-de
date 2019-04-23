---
title: 'Vorbereitung des Debugvorgangs: ASP.NET-Webanwendungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7a2640d39c90dc36a3960d230df46ac75bdbce6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092421"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Vorbereitung des Debugvorgangs: ASP.NET-Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Websitevorlage erstellt eine Web Forms-Anwendung. Wenn Sie mit dieser Vorlage eine Website erstellen, legt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die Standardeinstellungen für das Debuggen fest. In der **Projekteigenschaften** im Dialogfeld können Sie angeben, ob Sie die Webseite als Startseite einrichten möchten. Beim Starten des Debugvorgangs einen [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Website mit diesen Standardeinstellungen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] startet Internet Explorer, und fügt den Debugger an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Workerprozess (aspnet_wp.exe oder w3wp.exe). Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>So erstellen Sie eine Web Forms-Anwendung  
  
1. Auf der **Datei** Menü wählen **neue Website**.  
  
2. In der **neue Website** wählen Sie im Dialogfeld [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Website**.  
  
3. Klicken Sie auf **OK**.  
  
### <a name="to-debug-your-web-form"></a>So debuggen Sie Web Forms  
  
1. Legen Sie in den Funktionen und Ereignishandlern einen oder mehrere Haltepunkte fest.  
  
     Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Wenn ein Haltepunkt erreicht wird, wird der Code in der Funktion schrittweise durchlaufen. Achten Sie auf die Ausführung des Codes, bis Sie das Problem isolieren.  
  
     Weitere Informationen finden Sie unter [ausführen in Einzelschritten](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) und [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Ändern von Standardkonfigurationen  
 Bei Bedarf können Sie die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellten standardmäßigen Debug- und Releasekonfigurationen ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>So ändern Sie die Standarddebugkonfiguration  
  
1. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Website, und wählen Sie **Eigenschaftenseiten** zum Öffnen der **Eigenschaftenseiten** Dialogfeld.  
  
2. Klicken Sie auf **Startoptionen**.  
  
3. Legen Sie **Startaktion** an die Webseite, die zuerst angezeigt werden soll.  
  
4. Klicken Sie unter **Debugger**, stellen Sie sicher, dass **ASP.NET-Debuggen** ausgewählt ist.  
  
     Weitere Informationen finden Sie unter [Seiten Eigenschafteneinstellungen für Webprojekte](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
