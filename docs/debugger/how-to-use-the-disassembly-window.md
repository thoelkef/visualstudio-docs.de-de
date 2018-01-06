---
title: Anzeigen der Disassembly-Code im Debugger in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c53f5404eb127f2f5eb9ec844024beafaad22e86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Disassembly-Code im Visual Studio-Debugger anzeigen
Diese Funktion ist nur verfügbar, wenn Debuggen auf Adressebene aktiviert ist die **Optionen** Dialogfeld **Debuggen** Knoten. Es ist jedoch nicht für das Skript- oder SQL-Debuggen verfügbar.  
  
 Die **Disassembly** Fenster wird der Assemblycode, die vom Compiler erstellten Anweisungen entspricht. Beim Debuggen von verwaltetem Code entsprechen diese Assemblyanweisungen nicht der durch den Visual Studio-Compiler generierten Microsoft Intermediate Language (MSIL), sondern dem durch den Just-In-Time-Compiler (JIT) erstellten nativen Code.  
  
 Neben den Assemblyanweisungen der **Disassembly** Fenster kann die folgende optionale Informationen angezeigt:  
  
-   Speicheradresse, an der sich die einzelnen Anweisungen befinden. Bei systemeigenen Anwendungen ist dies die eigentliche Speicheradresse. Bei Visual Basic, C# oder verwaltetem Code ist dies ein Offset vom Beginn der Funktion.  
  
-   Quellcode, aus dem der Assemblercode abgeleitet wird.  
  
-   Codebytes – Bytedarstellungen der tatsächlichen Computer- oder MSIL-Anweisungen.  
  
-   Symbolnamen für die Speicheradressen.  
  
-   Mit dem Quellcode übereinstimmende Zeilennummern.  
  
 Assemblysprachanweisungen bestehen aus mnemonischen Codes (Abkürzungen für Anweisungsnamen) sowie Symbolen, die Variablen, Register und Konstanten darstellen. Jede Anweisung in Computercode wird durch mnemonischen Code in Assemblersprache dargestellt, dem in der Regel eine oder mehrere Variablen, Register oder Konstanten folgen.  
  
 Wenn Sie Assemblersprache nicht lesen können, aber trotzdem die Vorteile des Disassemblyfensters optimal nutzen möchten, sollten Sie sich ein gutes Buch über das Programmieren in Assemblersprache besorgen. Erläuterungen zum Programmieren in Assemblersprache würden jedoch den Rahmen dieser kurzen Einführung zum Disassemblyfenster sprengen.  
  
 Da Assemblercode in hohem Maße von Prozessorregistern abhängig ist (bzw. bei verwaltetem Code von Registern der Common Language Runtime), ist es häufig sinnvoll, das Disassemblyfenster zusammen mit dem Fenster Register zu verwenden, um dort den Registerinhalt untersuchen zu können.  
  
 Vermutlich wird es sich niemals als notwendig oder wünschenswert erweisen, Computercodeanweisungen nicht in Assemblersprache, sondern in ihrer  numerischen Rohdatenform anzuzeigen. Wenn Sie dies jedoch trotzdem tun möchten, können Sie hierfür das Fenster Arbeitsspeicher verwenden oder im Kontextmenü des Disassemblierungsfensters die Option Codebytes auswählen.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>So öffnen Sie das Disassemblierungsfenster  
  
-   Wählen Sie während des Debuggens, **Debuggen > Windows** , und klicken Sie dann auf **Disassembly**.
  
### <a name="to-turn-optional-information-on-or-off"></a>So aktivieren bzw. deaktivieren Sie die Anzeige optionaler Informationen  
  
-   Mit der rechten Maustaste die **Disassembly** Fenster, und aktivieren bzw. deaktivieren Sie die gewünschten Optionen im Kontextmenü.  
  
     Ein gelber Pfeil am linken Rand kennzeichnet die Position des aktuellen Ausführungspunkts. Bei nativem Code entspricht diese dem Programmzähler der CPU. Diese Position zeigt die nächste Anweisung an, die im Programm ausgeführt wird.  
  
     Weitere Informationen finden Sie unter [Paging oben oder unten im Arbeitsspeicher](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Gewusst wie: Verwenden des Fensters "Register"](../debugger/how-to-use-the-registers-window.md)