---
title: 'Vorgehensweise: Überprüfen von IIS-Eigenschafteneinstellungen | Microsoft-Dokumentation'
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
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 075581332a95f8cae03313adaf5fc2067910b217
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946426"
---
# <a name="how-to-verify-iis-property-settings"></a>Vorgehensweise: Überprüfen von IIS-Eigenschafteneinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Eigenschaften für eine Webanwendung mit dem IIS-Verwaltungstool festlegen. Diese Eigenschaften müssen korrekt festgelegt sein, damit die Anwendung ausgeführt werden kann. Das Überprüfen dieser Einstellungen ist daher ein häufig erforderlicher Schritt bei der Fehlerbehebung.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>So überprüfen Sie die IIS-Einstellungen der Webanwendung  
  
1.  Öffnen der **Verwaltung** Fenster: Auf der **starten** Startmenü **Programme**, und klicken Sie dann auf **Verwaltung**. Falls der Eintrag **Verwaltung** nicht im Menü **Programme** vorhanden ist, befindet er sich in der **Systemsteuerung**.  
  
    -   Unter Windows 2000 klicken Sie auf **Internetdienste-Manager**.  
  
    -   Unter Windows XP wählen Sie **Internetinformationsdienste**.  
  
    -   Unter Windows Server 2003 doppelklicken Sie auf **Serververwaltung**.  
  
         Das Fenster **Serververwaltung** wird geöffnet. Klicken Sie im Bereich **Anwendungsserver** auf **Diesen Anwendungsserver verwalten**.  
  
         Das Fenster **Anwendungsserver** wird geöffnet. Erweitern Sie im linken Bereich den Knoten **Internetinformationsdienste-Manager**.  
  
2.  Klicken Sie im Dialogfeld in der Strukturansicht auf den Knoten für den Computer. Klicken Sie auf den Knoten **Websites**, und wählen Sie den Knoten der Webanwendung aus. Dies ist entweder ein Websiteknoten (also ein gleichgeordneter Knoten des Knotens **Standardwebsite**) oder ein virtueller Verzeichnisknoten unter einem vorhandenen Websiteknoten.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Webanwendung, und klicken Sie im Kontextmenü auf **Eigenschaften**.  
  
4.  Überprüfen Sie die Sicherheitseinstellungen für die Webanwendung:  
  
    1.  Wählen Sie im **Eigenschaftenfenster** der Webanwendung die Registerkarte **Verzeichnissicherheit** aus, und klicken Sie auf **Bearbeiten**.  
  
    2.  Aktivieren Sie im Dialogfeld **Authentifizierungsmethoden** die Optionen **Anonymen Zugriff aktivieren** und **Integrierte Windows-Authentifizierung**, falls sie nicht bereits aktiviert sind.  
  
    3.  Klicken Sie auf **OK**, um das Dialogfeld **Authentifizierungsmethoden** zu schließen.  
  
5.  Bei ATL-Serveranwendungen müssen Sie sicherstellen, dass das Verb DEBUG mit der ISAPI-Erweiterung verknüpft ist. Weitere Informationen finden Sie unter [Vorgehensweise: Ordnen Sie DEBUG-Verb, mit der Erweiterung](http://msdn.microsoft.com/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Stellen Sie bei einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung sicher, dass für das virtuelle Verzeichnis der Anwendung in **Internetinformationsdienste-Manager**, **Internetdienste-Manager** bzw. **Internetinformationsdienste** ein Anwendungsname festgelegt ist.  
  
    1.  Klicken Sie im **Eigenschaftenfenster** der Webanwendung auf die Registerkarte **Verzeichnis**, wenn sich die Anwendung in einem virtuellen Verzeichnis befindet, bzw. auf die Registerkarte **Basisverzeichnis**, wenn sich die Anwendung in einer Website befindet.  
  
    2.  Vergewissern Sie sich, dass der Name in **Lokaler Pfad** mit dem Namen des Verzeichnisses übereinstimmt, in dem die Anwendung bereitgestellt wurde.  
  
    3.  Geben Sie unter **Anwendungseinstellungen** den Namen des Stammverzeichnisses ein, in dem die Anwendung enthalten ist.  
  
    4.  Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.  
  
7.  Klicken Sie bei einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung auf die Registerkarte **ASP.NET**, und vergewissern Sie sich, dass die richtige Version von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] angegeben ist.  
  
8.  Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.  
  
9. Klicken Sie auf **OK**, um das Dialogfeld **Internetinformationsdienste-Manager**, **Internetdienste-Manager** bzw. **Internetinformationsdienste** zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung](../debugger/debugging-web-applications-troubleshooting.md)
