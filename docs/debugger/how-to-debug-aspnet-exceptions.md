---
title: 'Vorgehensweise: Debuggen von ASP.NET-Ausnahmen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 002f100f11bd88e31b94283e7efe5e25299448bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944297"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Vorgehensweise: Debuggen von ASP.NET-Ausnahmen
Das Debuggen von Ausnahmen ist ein wichtiger Teil bei der Entwicklung einer robusten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung. Allgemeine Informationen zum Debuggen von Ausnahmen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Zum Debuggen von nicht behandelten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Ausnahmen muss sichergestellt sein, dass der Debugger dort anhält. Die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene. Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen. Um den Debugger anhalten, wenn eine Ausnahme ausgelöst wird, müssen Sie auswählen **Unterbrechen bei folgendem Ausnahmezustand: Wird ausgelöst,** für die jeweilige Ausnahme im Festlegen der **Ausnahmen** Dialogfeld.  
  
 Wenn Sie nur mein Code aktiviert haben **Unterbrechen bei folgendem Ausnahmezustand: Wird ausgelöst,** bewirkt nicht, dass den Debugger sofort unterbrochen wird, wenn eine Ausnahme in einer .NET Framework-Methode oder anderem Systemcode ausgelöst wird. Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht-Systemcode trifft, und dann unterbrochen. Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.  
  
 Nur mein Code bietet Ihnen eine weitere Möglichkeit, die sogar noch nützlicher sein können: **Unterbrechen Sie bei folgendem Ausnahmezustand: Vom Benutzercode unbehandelt**. Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird. Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>So aktivieren Sie Debuggen der ASP.NET-Ausnahmen mit Nur mein Code  
  
1.  Klicken Sie im Menü **Debuggen** auf **Ausnahmen**.  
  
     Das Dialogfeld **Ausnahmen** wird angezeigt.  
  
2.  Wählen Sie in der Zeile **Common Language Runtime-Ausnahmen** die Einstellung **Ausgelöst** oder **Vom Benutzercode unbehandelt** aus.  
  
     Wenn Sie die Einstellung **Vom Benutzercode unbehandelt** verwenden möchten, muss **Nur eigenen Code** aktiviert werden.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Empfohlene Vorgehensweise für die ASP.NET-Ausnahmebehandlung  
  
-   Platzieren Sie `try ... catch`-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können. Wenn die Anwendung beispielsweise Aufrufe an einen XML-Webdienst sendet oder direkt an eine SQL Server-Instanz, sollte dieser Code in **try … catch**-Blöcken enthalten sein, weil eine Reihe von Ausnahmen auftreten können.

## <a name="see-also"></a>Siehe auch
[Debug ASP.NET Applications (Debuggen von ASP.NET-Anwendungen)](../debugger/how-to-enable-debugging-for-aspnet-applications.md)