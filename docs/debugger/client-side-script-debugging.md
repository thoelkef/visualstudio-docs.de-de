---
title: Debuggen von clientseitigem Skript | Microsoft Docs
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f31897cc4fb48fd7c814d4d25cb41ce0cb7e57da
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464809"
---
# <a name="client-side-script-debugging"></a>Debuggen von clientseitigen Skripts
Der Visual Studio-Debugger stellt eine umfassende Debugumgebung zum Suchen und Beheben von Fehlern in clientseitigen Skripts auf ASP.NET-Seiten bereit.  
  
## <a name="opening-script-documents"></a>Öffnen von Skriptdokumenten  
Sie können Listen von serverseitigen und clientseitigen Skriptdokumente in finden Sie unter der **Projektmappen-Explorer** anzeigen. Sie können beliebige Skriptdokumente über den **Projektmappen-Explorer**öffnen. Weitere Informationen finden Sie unter [How to: View Script Documents](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Zuordnen von Haltepunkten  
 In Visual Studio können Sie serverseitigen Code nicht direkt debuggen, Sie können jedoch einen Haltepunkt in einer serverseitigen Datei festlegen. Visual Studio ordnet den Haltepunkt automatisch einer entsprechenden Position in der clientseitigen Datei zu und erstellt einen zugeordneten Haltepunkt im clientseitigen Code.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Manuelles oder automatisches Anhängen an Skripts  
 Um mit dem Debuggen von Skripts in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zu beginnen, muss der Debugger an das Skript anhängt werden, das Sie debuggen möchten. Dies kann manuell oder automatisch geschehen.  
  
 Sie können den Debugger manuell über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Debuggerschnittstelle anhängen und dabei einen laufenden Skriptprozess auswählen, an den der Debugger angehängt werden soll. Weitere Informationen finden Sie unter [How to: Attach to Script](../debugger/how-to-attach-to-script.md).  
  
 Der Debugger wird automatisch an das Skript angehängt, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Sie erreichen einen im Skript festgelegten Haltepunkt.  
  
-   Sie erreichen eine VBScript `Stop` -Anweisung oder JScript `debugger` -Anweisung im Skriptcode.  
  
-   Der Browser oder Server stellt einen Syntax- oder Laufzeitfehler im Skript fest. In diesem Fall wird ein Dialogfeld angezeigt, und Sie können mit dem Debuggen beginnen.  
  
 Wenn Sie den Debugger manuell an das Skript anhängen, wird der Skriptprozess weiterhin ausgeführt, bis er durch ein bestimmtes Ereignis angehalten wird. Sie können ihn anhalten, indem Sie im Menü **Debuggen** die Option **Unterbrechen** auswählen.  
  
 Wenn der Debugger automatisch angehängt wird, wird die Skriptausführung in der Zeile angehalten, in der der Haltepunkt, die `Stop` -Anweisung oder `debugger` -Anweisung bzw. der Fehler aufgetreten ist oder in der Sie das Debuggen in Internet Explorer ausgewählt haben.  
  
 Sie können jetzt die normalen Debuggerfunktionen verwenden, um das Debuggen zu starten. Beispielsweise können Sie die Befehle **Schritt** verwenden, um die Codeausführung zeilenweise fortzusetzen. Im Fenster **Aufrufliste** können Sie den Skriptfluss anzeigen und steuern. Sie können die Variablenfenster oder das **Direktfenster** verwenden, um Variablen und Eigenschaften anzuzeigen oder zu ändern.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Verbesserte Fehlermeldungen für das Skriptdebuggen  
 Visual Studio enthält verbesserte Fehlermeldungen für allgemeine Probleme beim Skriptdebuggen. Diese Meldungen werden erst angezeigt, wenn Sie den Debugger manuell an Internet Explorer anhängen. Wenn Sie beim automatischen Öffnen von Internet Explorer einen Fehlerzustand feststellen, sollten Sie versuchen, den Debugger manuell anzuhängen, damit die Fehlermeldungen angezeigt werden.  
  
## <a name="debugging-ajax-script-applications"></a>Debuggen von AJAX-Skriptanwendungen  
 AJAX-fähige Webanwendungen machen umfangreichen Gebrauch von Skriptcode und stellen besondere Anforderungen an das Debuggen. Weitere Informationen zu den Verfahrensweisen beim AJAX-Debuggen finden Sie unter  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Einschränkungen beim Skriptdebugging](../debugger/limitations-on-script-debugging.md)   
 [Variablenfenster](../debugger/debugger-windows.md)   
 [Direktfenster](../ide/reference/immediate-window.md)   
 [Debuggen und Tracing Ajax-Anwendungen (Übersicht)](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
