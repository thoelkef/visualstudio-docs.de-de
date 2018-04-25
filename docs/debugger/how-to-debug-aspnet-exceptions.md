---
title: 'Vorgehensweise: Debuggen von ASP.NET-Ausnahmen | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 5923818e93170ded1f857ac20d42cd6134aed5d3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-aspnet-exceptions"></a>Gewusst wie: Debuggen von ASP.NET-Ausnahmen
Debuggen von Ausnahmen ist ein wichtiger Bestandteil der Entwicklung einer robusten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendung. Allgemeine Informationen über das Debuggen von Ausnahmen ist am [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 So debuggen Sie nicht behandelte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Ausnahmen, müssen Sie sich vergewissern, dass der Debugger dort anhält. Die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene. Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen. Um den Debugger zu unterbrechen, wenn eine Ausnahme ausgelöst wird, müssen Sie auswählen **Unterbrechen bei folgendem Ausnahmezustand: ausgelöst** für die jeweilige Ausnahme im Festlegen der **Ausnahmen** (Dialogfeld).  
  
 Wenn Sie nur mein Code aktiviert haben **Unterbrechen bei folgendem Ausnahmezustand: ausgelöst** führt nicht dazu, dass den Debugger sofort an, wenn eine Ausnahme in einer .NET Framework-Methode oder anderem Systemcode ausgelöst wird. Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht-Systemcode trifft, und dann unterbrochen. Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.  
  
 Nur mein Code bietet Ihnen die Möglichkeit, die sogar noch nützlicher sein kann: **Unterbrechen bei folgendem Ausnahmezustand: vom Benutzercode unbehandelt**. Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird. Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>So aktivieren Sie Debuggen der ASP.NET-Ausnahmen mit Nur mein Code  
  
1.  Auf der **Debuggen** Menü klicken Sie auf **Ausnahmen**.  
  
     Die **Ausnahmen** Dialogfeld wird angezeigt.  
  
2.  Auf der **Common Language Runtime-Ausnahmen** Zeile **ausgelöst** oder **vom Benutzercode unbehandelt**.  
  
     Verwenden der **vom Benutzercode unbehandelt** festlegen, **nur mein Code** muss aktiviert sein...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Empfohlene Vorgehensweise für die ASP.NET-Ausnahmebehandlung  
  
-   Platzieren Sie `try ... catch`-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können. Z. B. wenn die Anwendung Aufrufe an einen XML-Webdienst oder direkt an einen SQL Server ist, diesen Code muss **try…catch** blockiert werden, da es gibt zahlreiche Ausnahmen, die auftreten können.

## <a name="see-also"></a>Siehe auch
[Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)