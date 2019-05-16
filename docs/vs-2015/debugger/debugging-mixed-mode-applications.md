---
title: Debuggen im gemischten Modus-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c8e9f36e7118b1681701f6c8ac60a5bc851308f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691359"
---
# <a name="debugging-mixed-mode-applications"></a>Debuggen von Anwendungen im gemischten Modus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Anwendung im gemischten Modus ist eine Anwendung, in der nativer Code (C++) mit verwaltetem Code (z. B. Visual Basic-Code, Visual C#-Code oder verwaltetes C++, das mit der Common Language Runtime ausgeführt wird) kombiniert wird. Das Debuggen von Anwendungen im gemischten Modus erfolgt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] weitestgehend transparent. Es unterscheidet sich nicht maßgeblich vom Debuggen einer Anwendung im einfachen Modus. Beachten Sie jedoch einige besondere Aspekte.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Aktivieren von "Bearbeiten und Fortfahren" in C++ beim Debuggen im gemischten Modus  
  
- Um "Bearbeiten und Fortfahren" für C++ in Visual Studio 2013 zu verwenden, müssen Sie die Legacyversion der Debug-Engine wiederherstellen. Informationen dazu finden Sie im Microsoft Application Lifecycle Management-Blogbeitrag [Switching to Managed Compatibility Mode in Visual Studio 2013 (Wechseln zum verwalteten Kompatibilitätsmodus in Visual Studio 2013)](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx)  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Auswertung von Eigenschaften in Anwendungen im gemischten Modus  
 In einer Anwendung im gemischten Modus erfordert die Auswertung von Eigenschaften durch den Debugger sehr viel Rechenleistung. Folglich werden Debugoperationen, z. B. das schrittweise Ausführen, scheinbar langsam ausgeführt. Weitere Informationen finden Sie unter [Stepping](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Falls Sie beim Debuggen im gemischten Modus einen Leistungsabfall beobachten, empfiehlt es sich u. U., die Eigenschaftenauswertung in den Debuggerfenstern zu deaktivieren.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>So deaktivieren Sie die Eigenschaftenauswertung  
  
1. Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2. Öffnen Sie im Dialogfeld **Optionen** den Ordner **Debuggen**, und wählen Sie die Kategorie **Allgemein** aus.  
  
3. Deaktivieren Sie das Kontrollkästchen **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**.  
  
   Da systemeigene Aufruflisten sich von verwalteten Aufruflisten unterscheiden, kann der Debugger nicht immer die vollständige Aufrufliste für den gemischten Code bereitstellen. Wenn systemeigener Code verwalteten Code aufruft, stellen Sie u. U. einige Diskrepanzen fest. Weitere Informationen finden Sie unter [Mixed Code and Missing Information in the Call Stack Window (Gemischter Code und fehlende Daten im Fenster „Aufrufliste“)](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
