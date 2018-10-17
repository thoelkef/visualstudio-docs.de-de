---
title: Just-In-Time, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
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
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5522c9da025b76a3892d3923cdd7397b8ed5ce5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207492"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Debuggen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für den Zugriff auf die **Just-In-Time-** wechseln Sie zur Seite der **Tools** Menü **Optionen**. In der **Optionen** Dialogfeld erweitern Sie die **Debuggen** Knoten, und wählen **Just-In-Time-**. Auf dieser Seite können Sie das Just-In-Time-Debuggen für verwalteten Code, nativen Code und Skripts aktivieren. Weitere Informationen finden Sie unter [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Sie können Just-In-Time-Debuggen für folgende Programmtypen aktivieren:  
  
-   Verwaltet  
  
-   Systemeigen  
  
-   Skript  
  
 Just-In-Time-Debuggen ist ein Verfahren zum Debuggen eines Programms, das außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gestartet wurde. Sie können ein in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstelltes Programm außerhalb der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung ausführen. Wenn Sie Just-In-Time-Debuggen aktiviert haben, wird bei einem Absturz ein Dialogfeld angezeigt, das Ihnen die Möglichkeit zum Debuggen bietet.  
  
## <a name="associated-warnings"></a>Zugeordnete Warnungen  
 Beim Besuch auf dieser Seite des der **Optionen** Dialogfeld möglicherweise eine Warnmeldung angezeigt:  
  
 **Ein anderer Debugger registriert hat sich selbst als die Just-In-Time-Debugger. Aktivieren Sie zur Reparatur Just-In-Time-debugging, oder führen Visual Studio-Reparatur aus.**  
  
 Diese Meldung wird angezeigt, wenn Sie einen anderen Debugger (möglicherweise eine ältere Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers) als Just-In-Time-Debugger festgelegt haben.  
  
 Eine andere Meldung, die Sie sehen könnten, ist:  
  
 **Just-In-Time Debuggen Registrierungsfehler. Aktivieren Sie zur Reparatur Just-In-Time-debugging, oder führen Visual Studio-Reparatur aus.**  
  
 Wenn Sie eine dieser Warnmeldungen, Just-In-Time-Debuggen mit finden Sie unter [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] sind Administratorrechte erforderlich, bis Sie das Problem behoben haben. Wenn Sie versuchen, Just-In-Time-Debuggen unter diesen Bedingungen zu aktivieren, obwohl Sie kein Administrator sind, wird die folgende Fehlermeldung angezeigt:  
  
 **Zugriff wird verweigert. Debuggen Sie ein Administrator Enable Just-In-Time- und reparieren Sie die Installation von Visual Studio.**  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen, Dialogfeld "Optionen"](../debugger/debugging-options-dialog-box.md)   
 [Gewusst wie: Angeben von Debuggereinstellungen](../debugger/how-to-specify-debugger-settings.md)



