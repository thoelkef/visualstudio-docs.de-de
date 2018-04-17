---
title: 'Vorgehensweise: Überprüfen Sie die IIS-Eigenschafteneinstellungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b351f45d8e45116894d08f4a813e7c427f4cb5c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-verify-iis-property-settings"></a>Gewusst wie: Überprüfen von IIS-Eigenschafteneinstellungen
Sie können die Eigenschaften für eine Webanwendung mit dem IIS-Verwaltungstool festlegen. Diese Eigenschaften müssen korrekt festgelegt sein, damit die Anwendung ausgeführt werden kann. Das Überprüfen dieser Einstellungen ist daher ein häufig erforderlicher Schritt bei der Fehlerbehebung.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>So überprüfen Sie die IIS-Einstellungen der Webanwendung  
  
1.  Öffnen der **Verwaltung** Fenster: auf die **starten** Sie im Menü **Programme**, und klicken Sie dann auf **Verwaltung**. Wenn **Verwaltung** erscheint nicht in der **Programme** Menü, und klicken Sie dann auf befindet er sich in der **Systemsteuerung**.  
  
    -   Wählen Sie auf Windows 2000, **Internetdienste-Manager**.  
  
    -   Wählen Sie unter Windows XP **Internetinformationsdienste (IIS)**.  
  
    -   Doppelklicken Sie auf Windows Server 2003 auf **Serververwaltung**.  
  
         Die **Serververwaltung** Fenster wird geöffnet. Klicken Sie unter **Anwendungsserver**, klicken Sie auf **diesen Anwendungsserver verwalten**.  
  
         Die **Anwendungsserver** Fenster wird geöffnet. Öffnen der **(Internet Information Services, IIS) Manager** im linken Bereich den Knoten.  
  
2.  Klicken Sie im Dialogfeld in der Strukturansicht auf den Knoten für den Computer. Klicken Sie auf die **Websites** Knoten, und wählen Sie die Webanwendung-Knoten. Sie werden entweder ein Websiteknoten und somit ein gleichgeordnetes Element von der **Default Web Site** Knoten oder ein virtueller Verzeichnisknoten unter einem vorhandenen Websiteknoten.  
  
3.  Maustaste auf die Webanwendung, und klicken Sie im Kontextmenü auf **Eigenschaften**.  
  
4.  Überprüfen Sie die Sicherheitseinstellungen für die Webanwendung:  
  
    1.  In der Webanwendung **Eigenschaften** Fenster, klicken Sie auf die **Verzeichnissicherheit** Registerkarte, und klicken Sie auf **bearbeiten**.  
  
    2.  In der **Authentifizierungsmethoden** wählen Sie im Dialogfeld **anonymen Zugriff aktivieren** und **integrierte Windows-Authentifizierung** , wenn sie nicht bereits aktiviert sind.  
  
    3.  Klicken Sie auf **OK** schließen die **Authentifizierungsmethoden** (Dialogfeld).  
  
5.  Bei ATL-Serveranwendungen müssen Sie sicherstellen, dass das Verb DEBUG mit der ISAPI-Erweiterung verknüpft ist. Weitere Informationen finden Sie unter [Vorgehensweise: DEBUGGEN Verb zuordnen, mit der Erweiterung](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendung, vergewissern Sie sich das virtuelle Verzeichnis für die Anwendung ein Anwendungsname festgelegt hat **(Internet Information Services, IIS) Manager**, **Internetdienste-Manager** oder  **Internetinformationsdienste (IIS)**.  
  
    1.  In der Webanwendung **Eigenschaften** wählen die **Directory** Registerkarte, wenn die Anwendung in ein virtuelles Verzeichnis ist oder die **Basisverzeichnis** Registerkarte, wenn die Anwendung wird eine Website.  
  
    2.  Überprüfen Sie, ob der Name in der **lokaler Pfad** entspricht dem Namen des Verzeichnisses, in dem die Anwendung bereitgestellt wurde.  
  
    3.  Klicken Sie unter **Anwendungseinstellungen**, geben Sie den Namen des Stammverzeichnisses, die die Anwendung enthält.  
  
    4.  Klicken Sie auf **OK** schließen die **Eigenschaften** (Dialogfeld).  
  
7.  Für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendung, klicken Sie auf die **ASP.NET** Registerkarte, und überprüfen Sie, ob die richtige Version des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] angegeben ist.  
  
8.  Klicken Sie auf **OK** schließen die **Eigenschaften** (Dialogfeld).  
  
9. Klicken Sie auf **OK** schließen die **(Internet Information Services, IIS) Manager**, **Internetdienste-Manager**, oder **Internetinformationsdienste (IIS)**(Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung](../debugger/debugging-web-applications-troubleshooting.md)