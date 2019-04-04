---
title: Just-In-Time, Debuggen, Dialogfeld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960135"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Debuggen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Seite **Just-In-Time** zu öffnen, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Debuggen**, und klicken Sie auf **Just-In-Time**. Auf dieser Seite können Sie das Just-In-Time-Debuggen für verwalteten Code, nativen Code und Skripts aktivieren. Weitere Informationen hierzu finden Sie unter [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Sie können Just-In-Time-Debuggen für folgende Programmtypen aktivieren:  
  
- Verwaltet  
  
- Systemeigen  
  
- Skript  
  
  Just-In-Time-Debuggen ist ein Verfahren zum Debuggen eines Programms, das außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gestartet wurde. Sie können ein in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstelltes Programm außerhalb der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung ausführen. Wenn Sie Just-In-Time-Debuggen aktiviert haben, wird bei einem Absturz ein Dialogfeld angezeigt, das Ihnen die Möglichkeit zum Debuggen bietet.  
  
## <a name="associated-warnings"></a>Zugeordnete Warnungen  
 Wenn Sie diese Seite des Dialogfelds **Optionen** anzeigen, wird möglicherweise folgende Warnmeldung angezeigt:  
  
 **Ein anderer Debugger hat sich als Just-In-Time-Debugger registriert. Aktivieren Sie zur Reparatur das Just-In-Time-Debugging, oder führen Sie die Visual Studio-Reparatur aus.**  
  
 Diese Meldung wird angezeigt, wenn Sie einen anderen Debugger (möglicherweise eine ältere Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers) als Just-In-Time-Debugger festgelegt haben.  
  
 Eine andere Meldung, die Sie sehen könnten, ist:  
  
 **Registrierungsfehler für Just-In-Time-Debugging. Aktivieren Sie zur Reparatur das Just-In-Time-Debugging, oder führen Sie die Visual Studio-Reparatur aus.**  
  
 Wenn eine dieser Warnmeldungen angezeigt wird, sind für das Just-In-Time-Debuggen mit [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Administratorrechte erforderlich, bis Sie das Problem behoben haben. Wenn Sie versuchen, Just-In-Time-Debuggen unter diesen Bedingungen zu aktivieren, obwohl Sie kein Administrator sind, wird die folgende Fehlermeldung angezeigt:  
  
 **Zugriff verweigert. Lassen Sie einen Administrator das Just-In-Time-Debugging aktivieren oder die Installation von Visual Studio reparieren.**  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen, Dialogfeld „Optionen“](../debugger/debugging-options-dialog-box.md)   
 [Vorgehensweise: Angeben von Debuggereinstellungen](../debugger/how-to-specify-debugger-settings.md)
