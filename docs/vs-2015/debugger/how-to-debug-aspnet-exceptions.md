---
title: 'Vorgehensweise: Debuggen von ASP.NET-Ausnahmen | Microsoft-Dokumentation'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205422"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Vorgehensweise: Debuggen von ASP.NET-Ausnahmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen von Ausnahmen ist ein wichtiger Teil bei der Entwicklung einer robusten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung. Allgemeine Informationen zum Debuggen von Ausnahmen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Zum Debuggen von nicht behandelten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Ausnahmen muss sichergestellt sein, dass der Debugger dort anhält. Die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene. Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen. Um den Debugger beim Auslösen einer Ausnahme zu unterbrechen, müssen Sie die Einstellung **Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst** für diese bestimmte Ausnahme im Dialogfeld **Ausnahmen** auswählen.  
  
 Falls die Option „Nur eigenen Code“ aktiviert ist, hält der Debugger bei **Break when an exception is: Thrown** (Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst) nicht sofort an, wenn eine Ausnahme in einer .NET Framework-Methode oder anderem Systemcode ausgelöst wird. Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht-Systemcode trifft, und dann unterbrochen. Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.  
  
 Die Einstellung „Nur eigenen Code“ stellt Ihnen eine weitere Option zur Verfügung, die sogar noch nützlicher sein kann: **Unterbrechen bei folgendem Ausnahmezustand: Vom Benutzercode unbehandelt**. Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird. Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>So aktivieren Sie Debuggen der ASP.NET-Ausnahmen mit Nur mein Code  
  
1. Klicken Sie im Menü **Debuggen** auf **Ausnahmen**.  
  
     Das Dialogfeld **Ausnahmen** wird angezeigt.  
  
2. Wählen Sie in der Zeile **Common Language Runtime-Ausnahmen** die Einstellung **Ausgelöst** oder **Vom Benutzercode unbehandelt** aus.  
  
     Wenn Sie die Einstellung **Vom Benutzercode unbehandelt** verwenden möchten, muss **Nur eigenen Code** aktiviert werden.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Empfohlene Vorgehensweise für die ASP.NET-Ausnahmebehandlung  
  
- Platzieren Sie `try … catch`-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können. Wenn die Anwendung z. b. Aufrufe an einen XML-Webdienst oder direkt an einen SQL Server sendet, sollte dieser Code in **try... Catch** -Blöcke, da zahlreiche Ausnahmen auftreten können.
