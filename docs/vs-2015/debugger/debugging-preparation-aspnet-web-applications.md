---
title: 'Vorbereitung zum Debuggen: ASP.NET-Webanwendungen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691463"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Vorbereitung zum Debuggen: ASP.NET-Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Website [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Vorlage erstellt eine Web Form-Anwendung. Wenn Sie mit dieser Vorlage eine Website erstellen, legt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die Standardeinstellungen für das Debuggen fest. Im Dialogfeld **Projekteigenschaften** können Sie angeben, ob die Webseite eine Startseite sein soll. Wenn Sie mit dem Debuggen einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Website mit diesen Standardeinstellungen beginnen, wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Internet Explorer von gestartet und der Debugger an den Arbeits [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Prozess (aspnet_wp.exe oder w3wp.exe) angefügt. Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>So erstellen Sie eine Web Forms-Anwendung  
  
1. Wählen Sie im Menü **Datei** die Option **neue Website**aus.  
  
2. Wählen Sie im Dialogfeld **neue Website** die Option [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Website**aus.  
  
3. Klicken Sie auf **OK**.  
  
### <a name="to-debug-your-web-form"></a>So debuggen Sie Web Forms  
  
1. Legen Sie in den Funktionen und Ereignishandlern einen oder mehrere Haltepunkte fest.  
  
     Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Wenn ein Haltepunkt erreicht wird, wird der Code in der Funktion schrittweise durchlaufen. Achten Sie auf die Ausführung des Codes, bis Sie das Problem isolieren.  
  
     Weitere Informationen finden Sie unter [Schritt](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) -und [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Ändern von Standardkonfigurationen  
 Bei Bedarf können Sie die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellten standardmäßigen Debug- und Releasekonfigurationen ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>So ändern Sie die Standarddebugkonfiguration  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Website, und wählen Sie **Eigenschaften Seiten** aus, um das Dialogfeld **Eigenschaften Seiten** zu öffnen.  
  
2. Klicken Sie auf **Start Optionen**.  
  
3. Legen Sie die **Start Aktion** auf die Webseite fest, die zuerst angezeigt werden soll.  
  
4. Vergewissern Sie sich unter **Debugger**, dass **ASP.NET Debugging** ausgewählt ist.  
  
     Weitere Informationen finden Sie unter [Eigenschaften Seiteneinstellungen für Webprojekte](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debugger-Grundlagen](../debugger/debugger-basics.md)   
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
