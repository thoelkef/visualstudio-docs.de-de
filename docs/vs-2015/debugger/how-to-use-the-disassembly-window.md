---
title: 'Vorgehensweise: Verwenden des Disassembierungsfensters | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
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
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42d7c9798527498f2803d814515faefd62c3ace9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077497"
---
# <a name="how-to-use-the-disassembly-window"></a>Vorgehensweise: Verwenden des Disassembierungsfensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Feature ist nur verfügbar, wenn Debuggen auf Adressebene aktiviert, ist die **Optionen** Dialogfeld **Debuggen** Knoten. Es ist jedoch nicht für das Skript- oder SQL-Debuggen verfügbar.  
  
 Im Fenster **Disassemblierung** wird der Assemblycode angezeigt, der den vom Compiler erstellten Anweisungen entspricht. Beim Debuggen von verwaltetem Code entsprechen diese Assemblyanweisungen nicht der durch den Visual Studio-Compiler generierten Microsoft Intermediate Language (MSIL), sondern dem durch den Just-In-Time-Compiler (JIT) erstellten systemeigenen Code.  
  
 Neben den Assemblyanweisungen können folgende optionale Informationen im Fenster **Disassemblierung** angezeigt werden:  
  
- Speicheradresse, an der sich die einzelnen Anweisungen befinden. Bei systemeigenen Anwendungen ist dies die eigentliche Speicheradresse. Bei Visual Basic, C# oder verwaltetem Code ist dies ein Offset vom Beginn der Funktion.  
  
- Quellcode, aus dem der Assemblercode abgeleitet wird.  
  
- Codebytes – Bytedarstellungen der tatsächlichen Computer- oder MSIL-Anweisungen.  
  
- Symbolnamen für die Speicheradressen.  
  
- Mit dem Quellcode übereinstimmende Zeilennummern.  
  
  Assemblysprachanweisungen bestehen aus mnemonischen Codes (Abkürzungen für Anweisungsnamen) sowie Symbolen, die Variablen, Register und Konstanten darstellen. Jede Anweisung in Computercode wird durch mnemonischen Code in Assemblersprache dargestellt, dem in der Regel eine oder mehrere Variablen, Register oder Konstanten folgen.  
  
  Wenn Sie Assemblersprache nicht lesen können, aber trotzdem die Vorteile des Disassemblyfensters optimal nutzen möchten, sollten Sie sich ein gutes Buch über das Programmieren in Assemblersprache besorgen. Erläuterungen zum Programmieren in Assemblersprache würden jedoch den Rahmen dieser kurzen Einführung zum Disassemblyfenster sprengen.  
  
  Da Assemblercode in hohem Maße von Prozessorregistern abhängig ist (bzw. bei verwaltetem Code von Registern der Common Language Runtime), ist es häufig sinnvoll, das Disassemblyfenster zusammen mit dem Fenster Register zu verwenden, um dort den Registerinhalt untersuchen zu können.  
  
  Vermutlich wird es sich niemals als notwendig oder wünschenswert erweisen, Computercodeanweisungen nicht in Assemblersprache, sondern in ihrer  numerischen Rohdatenform anzuzeigen. Wenn Sie dies jedoch trotzdem tun möchten, können Sie hierfür das Fenster Arbeitsspeicher verwenden oder im Kontextmenü des Disassemblierungsfensters die Option Codebytes auswählen.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>So öffnen Sie das Disassemblierungsfenster  
  
- Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Disassembly**.  
  
     Der Debugger muss ausgeführt werden oder sich im Unterbrechungsmodus befinden.  
  
### <a name="to-turn-optional-information-on-or-off"></a>So aktivieren bzw. deaktivieren Sie die Anzeige optionaler Informationen  
  
- Mit der rechten Maustaste die **Disassembly** Fenster, und aktivieren bzw. deaktivieren Sie die gewünschten Optionen im Kontextmenü die Option.  
  
     Ein gelber Pfeil am linken Rand kennzeichnet die Position des aktuellen Ausführungspunkts. Bei systemeigenem Code entspricht diese dem Programmzähler der CPU. Diese Position zeigt die nächste Anweisung an, die im Programm ausgeführt wird.  
  
     Weitere Informationen finden Sie unter [Paging oben oder unten im Arbeitsspeicher](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Vorgehensweise: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)
