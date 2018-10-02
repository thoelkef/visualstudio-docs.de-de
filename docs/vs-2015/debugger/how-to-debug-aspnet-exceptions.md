---
title: 'Vorgehensweise: Debuggen von ASP.NET-Ausnahmen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d37a67fd0b25de79ceb764e9e80884b97310a307
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512231"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Gewusst wie: Debuggen von ASP.NET-Ausnahmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Debuggen von ASP.NET-Ausnahmen](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-aspnet-exceptions).  
  
Debuggen von Ausnahmen ist ein wichtiger Bestandteil der Entwicklung einer robusten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Anwendung. Allgemeine Informationen zum Debuggen von Ausnahmen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 So debuggen Sie nicht behandelte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Ausnahmen, achten Sie darauf, dass der Debugger dort anhält. Die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene. Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen. Um den Debugger anhalten, wenn eine Ausnahme ausgelöst wird, müssen Sie auswählen **Unterbrechen bei folgendem Ausnahmezustand: ausgelöst** Einstellung für die jeweilige Ausnahme im der **Ausnahmen** Dialogfeld.  
  
 Wenn Sie nur mein Code aktiviert haben **Unterbrechen bei folgendem Ausnahmezustand: ausgelöst** bewirkt nicht, dass den Debugger sofort unterbrochen wird, wenn eine Ausnahme in einer .NET Framework-Methode oder anderem Systemcode ausgelöst wird. Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht-Systemcode trifft, und dann unterbrochen. Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.  
  
 Nur mein Code bietet Ihnen die Möglichkeit, die sogar noch nützlicher sein können: **Unterbrechen bei folgendem Ausnahmezustand: vom Benutzercode unbehandelt**. Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird. Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>So aktivieren Sie Debuggen der ASP.NET-Ausnahmen mit Nur mein Code  
  
1.  Auf der **Debuggen** Menü klicken Sie auf **Ausnahmen**.  
  
     Die **Ausnahmen** Dialogfeld wird angezeigt.  
  
2.  Auf der **Common Language Runtime-Ausnahmen** Zeile **ausgelöst** oder **vom Benutzercode unbehandelt**.  
  
     Verwenden der **vom Benutzercode unbehandelt** Einstellung **nur mein Code** muss aktiviert sein...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Empfohlene Vorgehensweise für die ASP.NET-Ausnahmebehandlung  
  
-   Platzieren Sie `try … catch`-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können. Z. B. wenn die Anwendung Aufrufe an einen XML-Webdienst oder direkt an eine SQL Server herstellt, diesen Code muss **try … Catch** blockiert wird, weil es gibt zahlreiche Ausnahmen, die auftreten können.



