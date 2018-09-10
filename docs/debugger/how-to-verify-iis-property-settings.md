---
title: 'Vorgehensweise: Überprüfen von IIS-Eigenschafteneinstellungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 0c7bef881efeb25bc5ec19a3451412816d19534b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281494"
---
# <a name="how-to-verify-iis-property-settings"></a>Gewusst wie: Überprüfen von IIS-Eigenschafteneinstellungen
Sie können die Eigenschaften für eine Webanwendung mit dem IIS-Verwaltungstool festlegen. Diese Eigenschaften müssen korrekt festgelegt sein, damit die Anwendung ausgeführt werden kann. Das Überprüfen dieser Einstellungen ist daher ein häufig erforderlicher Schritt bei der Fehlerbehebung.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>So überprüfen Sie die IIS-Einstellungen der Webanwendung  
  
1.  Öffnen der **Verwaltung** Fenster: auf die **starten** , zeigen Sie auf **Programme**, und klicken Sie dann auf **Verwaltung**. Wenn **Verwaltung** erscheint nicht in der **Programme** Menü und dann befindet er sich in der **Systemsteuerung**.  
  
    -   Wählen Sie auf Windows 2000, **Internetdienste-Manager**.  
  
    -   Wählen Sie unter Windows XP **Internet Information Services**.  
  
    -   Doppelklicken Sie auf Windows Server 2003 auf **Serververwaltung**.  
  
         Die **Serververwaltung** Fenster wird geöffnet. Klicken Sie unter **Anwendungsserver**, klicken Sie auf **diesen Anwendungsserver verwalten**.  
  
         Die **Anwendungsserver** Fenster wird geöffnet. Öffnen der **(Internet Information Services, IIS) Manager** im linken Bereich den Knoten.  
  
2.  Klicken Sie im Dialogfeld in der Strukturansicht auf den Knoten für den Computer. Klicken Sie auf die **Websites** Knoten, und wählen Sie die Webanwendung aus. Sie werden entweder ein Websiteknoten und somit ein gleichgeordnetes Element von der **Default Web Site** Knoten oder ein virtueller Verzeichnisknoten unter einem vorhandenen Websiteknoten.  
  
3.  Mit der rechten Maustaste in der Webanwendung, und klicken Sie im Kontextmenü auf **Eigenschaften**.  
  
4.  Überprüfen Sie die Sicherheitseinstellungen für die Webanwendung:  
  
    1.  In der Webanwendung **Eigenschaften** Fenster, klicken Sie auf die **Verzeichnissicherheit** Registerkarte, und klicken Sie auf **bearbeiten**.  
  
    2.  In der **Authentifizierungsmethoden** wählen Sie im Dialogfeld **anonymen Zugriff aktivieren** und **integrierte Windows-Authentifizierung** , wenn sie nicht bereits aktiviert sind.  
  
    3.  Klicken Sie auf **OK** schließen die **Authentifizierungsmethoden** Dialogfeld.  
  
5.  Bei ATL-Serveranwendungen müssen Sie sicherstellen, dass das Verb DEBUG mit der ISAPI-Erweiterung verknüpft ist. Weitere Informationen finden Sie unter [Vorgehensweise: Zuordnen von DEBUG Verb mit der Erweiterung](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung, stellen Sie sicher des virtuellen Ordners ist für die Anwendung einen Anwendungsnamen ein, legen Sie in hat **(Internet Information Services, IIS) Manager**, **Internetdienste-Manager** oder  **Internet-Informationsdienste**.  
  
    1.  In der Webanwendung **Eigenschaften** wählen Sie im Fenster der **Directory** Registerkarte, wenn die Anwendung in einem virtuellen Verzeichnis befindet oder der **Basisverzeichnis** Registerkarte, wenn die Anwendung in eine Website.  
  
    2.  Überprüfen Sie, ob der Name in der **lokaler Pfad** entspricht dem Namen des Verzeichnisses, in dem die Anwendung bereitgestellt wurde.  
  
    3.  Klicken Sie unter **Anwendungseinstellungen**, geben Sie den Namen des Stammverzeichnisses, der Anwendung enthält.  
  
    4.  Klicken Sie auf **OK** schließen die **Eigenschaften** Dialogfeld.  
  
7.  Für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung, klicken Sie auf die **ASP.NET** Registerkarte, und überprüfen Sie, ob die richtige Version der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] angegeben ist.  
  
8.  Klicken Sie auf **OK** schließen die **Eigenschaften** Dialogfeld.  
  
9. Klicken Sie auf **OK** schließen die **(Internet Information Services, IIS) Manager**, **Internetdienste-Manager**, oder **Internet Information Services**Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung](../debugger/debugging-web-applications-troubleshooting.md)