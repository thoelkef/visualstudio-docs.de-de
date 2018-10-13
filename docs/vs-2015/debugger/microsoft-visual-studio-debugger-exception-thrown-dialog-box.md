---
title: Microsoft Visual Studio Debugger (Ausnahmeverweis) Dialogfeld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c3ce3a3362c657d4302ba919c866d4a32055423
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226163"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (Ausnahmeverweis) (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Programm ist eine Ausnahme aufgetreten. In diesem Dialogfeld wird die Art der ausgelösten Ausnahme angezeigt. Die Ausnahme muss durch den Code behandelt werden. Folgende Optionen stehen für das Behandeln der Ausnahme zur Verfügung:  
  
 **Break**  
 Die Ausführung wird im Debugger unterbrochen. Der Ausnahmehandler wird vor der Unterbrechung nicht aufgerufen. Wenn Sie ab der Unterbrechung fortsetzen, wird der Ausnahmehandler aufgerufen.  
  
 **Continue**  
 Die Ausführung wird fortgesetzt, sodass der die Ausnahme vom Ausnahmehandler behandelt werden kann. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar. **Weiterhin** kann die Anwendung aus, um den Vorgang fortzusetzen. In einer systemeigenen Anwendung wird die Ausnahme bei dieser Option erneut ausgelöst. In einer verwalteten Anwendung wird dadurch entweder das Programm beendet oder die Ausnahme wird von einer Hostanwendung behandelt.  
  
> [!NOTE]
>  In verwaltetem Code können Sie die Ausführung nach einem Ausnahmefehler nicht fortsetzen. Auswahl **Weiter** nach der eine nicht behandelte Ausnahme in verwaltetem Code wird das Debuggen zu beenden.  
  
 **Ignorieren**  
 Diese Option ermöglicht das Fortsetzen der Ausführung ohne Aufrufen des Ausnahmehandlers. Dies kann sich weiter auswirken und beispielsweise zu weiteren Ausnahmen und Fehlern führen. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Bewährte Methoden für Ausnahmen](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Ausnahmebehandlung](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)



