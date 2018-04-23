---
title: 'Vorgehensweise: Debuggen von eingefügtem Code | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf602d8ee670e5fce8602cb50d2aaa1066b501de
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-injected-code"></a>Gewusst wie: Debuggen von eingefügtem Code
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Die Verwendung von Attributen kann die C++-Programmierung erheblich vereinfachen. Weitere Informationen finden Sie unter [Konzepte](/cpp/windows/attributed-programming-concepts). Einige Attribute werden direkt vom Compiler interpretiert. Andere Attribute fügen Code in den Programmquellcode ein, der anschließend vom Compiler kompiliert wird. Dieser eingefügte Code kann die Programmierung vereinfachen, da weniger Code geschrieben werden muss. Manchmal kann die Anwendung jedoch aufgrund eines Fehlers fehlschlagen, der beim Ausführen von eingefügtem Code auftritt. In diesem Fall möchten Sie den eingefügten Code wahrscheinlich überprüfen. Visual Studio bietet zwei Möglichkeiten, eingefügten Code zu überprüfen:  
  
-   Sehen Sie eingefügten Code in der **Disassembly** Fenster.  
  
-   Mit [/FX](/cpp/build/reference/fx-merge-injected-code), Sie können eine zusammengeführte Quelldatei, die ursprünglichen als auch eingefügten Code enthält erstellen.  
  
 Die **Disassembly** Fenster zeigt Assemblysprachanweisungen, die dem Quellcode und den mittels Attributen eingefügten Code entsprechen. Darüber hinaus die **Disassembly** Fenster kann die Quellcode Anmerkung anzeigen.  
  
### <a name="to-turn-on-source-annotation"></a>So aktivieren Sie Quellcodeanmerkungen  
  
-   Mit der rechten Maustaste die **Disassembly** Fenster, und wählen Sie **Quellcode anzeigen** aus dem Kontextmenü.  
  
     Wenn Sie den Speicherort eines Attributs in einem Quellcodefenster kennen, können Sie mithilfe des Kontextmenüs finden in den eingefügten Code die **Disassembly** Fenster.  
  
### <a name="to-view-injected-code"></a>So zeigen Sie eingefügten Code an  
  
1.  Der Debugger muss sich im Unterbrechungsmodus befinden.  
  
2.  Positionieren Sie den Cursor im Quellcodefenster vor dem Attribut, dessen eingefügter Code angezeigt werden soll.  
  
3.  Mit der rechten Maustaste, und wählen Sie **Gehe zu Disassembly** aus dem Kontextmenü.  
  
     Wenn das Attribut in der Nähe des aktuellen Ausführungspunktes befindet, können Sie auswählen der **Disassembly** Fenster aus der **Debuggen** Menü.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>So zeigen Sie den Disassemblycode am aktuellen Ausführungspunkt an  
  
1.  Der Debugger muss sich im Unterbrechungsmodus befinden.  
  
2.  Aus der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Disassembly**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)