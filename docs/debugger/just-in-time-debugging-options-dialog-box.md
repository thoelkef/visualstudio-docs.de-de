---
title: Just-In-Time, Debuggen, Dialogfeld "Optionen" | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 057c5e0e37d8e84daa4348c91847a12b6a9ae5e9
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Debuggen, Dialogfeld "Optionen"
Für den Zugriff auf die **Just-in-Time** Seite, wechseln Sie zu der **Tools** Menü, und klicken Sie auf **Optionen**. In der **Optionen** Dialogfeld erweitern Sie die **Debuggen** Knoten, und wählen **Just-in-Time**. Auf dieser Seite können Sie das Just-In-Time-Debuggen für verwalteten Code, nativen Code und Skripts aktivieren. Weitere Informationen finden Sie unter [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Sie können Just-In-Time-Debuggen für folgende Programmtypen aktivieren:  
  
-   Verwaltet  
  
-   Systemeigen  
  
-   Skript  
  
 Just-In-Time-Debuggen ist ein Verfahren zum Debuggen eines Programms, das außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestartet wurde. Sie können ein in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstelltes Programm außerhalb der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Umgebung ausführen. Wenn Sie Just-In-Time-Debuggen aktiviert haben, wird bei einem Absturz ein Dialogfeld angezeigt, das Ihnen die Möglichkeit zum Debuggen bietet.  
  
## <a name="associated-warnings"></a>Zugeordnete Warnungen  
 Auf dieser Seite des beim Besuch der **Optionen** (Dialogfeld), möglicherweise eine Warnmeldung angezeigt:  
  
 **Ein anderer Debugger hat sich selbst als Just-in-Time registriert Debugger. Aktivieren Sie zur Reparatur Just-in-Time-debugging, oder führen Visual Studio-Reparatur aus.**  
  
 Diese Meldung wird angezeigt, wenn Sie einen anderen Debugger (möglicherweise eine ältere Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debuggers) als Just-In-Time-Debugger festgelegt haben.  
  
 Eine andere Meldung, die Sie sehen könnten, ist:  
  
 **Just-in-Time Debuggen Registrierungsfehler. Aktivieren Sie zur Reparatur Just-in-Time-debugging, oder führen Visual Studio-Reparatur aus.**  
  
 Wenn Sie eine dieser Warnmeldungen Just-in-Time-Debuggen mit finden Sie unter [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sind Administratorrechte erforderlich, bis Sie das Problem behoben haben. Wenn Sie versuchen, Just-In-Time-Debuggen unter diesen Bedingungen zu aktivieren, obwohl Sie kein Administrator sind, wird die folgende Fehlermeldung angezeigt:  
  
 **Der Zugriff wird verweigert. Haben Sie ein Administrator aktivieren Sie Just-in-Time-Debuggen, oder reparieren Sie die Installation von Visual Studio.**  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen, Dialogfeld "Optionen"](../debugger/debugging-options-dialog-box.md)   
 [Gewusst wie: Angeben von Debuggereinstellungen](../debugger/how-to-specify-debugger-settings.md)