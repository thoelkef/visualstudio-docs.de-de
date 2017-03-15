---
title: "Gewusst wie: Debuggen von eingef&#252;gtem Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.injected"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Assemblysprache, Anzeigen"
  - "Debuggen [C++], Aktivieren von Quellcodeanmerkungen"
  - "Debuggen [C++], Eingefügter Code"
  - "Debuggen [C++], Verwenden von Attributen"
  - "Debuggen [C++], Anzeigen von Assemblycode"
  - "Disassemblycode, Debuggen"
  - "Eingefügter Code"
  - "Quellcode anzeigen (Befehl) [Debugger]"
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Debuggen von eingef&#252;gtem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Die Verwendung von Attributen kann die C\+\+\-Programmierung erheblich vereinfachen.  Weitere Informationen finden Sie unter [Concepts](/visual-cpp/windows/attributed-programming-concepts).  Einige Attribute werden direkt vom Compiler interpretiert.  Andere Attribute fügen Code in den Programmquellcode ein, der anschließend vom Compiler kompiliert wird.  Dieser eingefügte Code kann die Programmierung vereinfachen, da weniger Code geschrieben werden muss.  Manchmal kann die Anwendung jedoch aufgrund eines Fehlers fehlschlagen, der beim Ausführen von eingefügtem Code auftritt.  In diesem Fall möchten Sie den eingefügten Code wahrscheinlich überprüfen.  Visual Studio bietet zwei Möglichkeiten, eingefügten Code zu überprüfen:  
  
-   Eingefügter Code kann im **Disassemblyfenster** angezeigt werden.  
  
-   Mit [\/Fx](/visual-cpp/build/reference/fx-merge-injected-code) lässt sich eine zusammengeführte Quelldatei erstellen, die sowohl Original\- als auch eingefügten Code enthält.  
  
 Im **Disassemblyfenster** werden Assemblysprachanweisungen angezeigt, die für den Quellcode sowie für den mittels Attributen eingefügten Code stehen.  Darüber hinaus können im **Disassemblyfenster** Quellcodeanmerkungen angezeigt werden.  
  
### So aktivieren Sie Quellcodeanmerkungen  
  
-   Klicken Sie mit der rechten Maustaste in das **Disassemblyfenster**, und klicken Sie im Kontextmenü auf **Quellcode anzeigen**.  
  
     Wenn Sie wissen, an welcher Stelle sich ein Attribut im Quellcodefenster befindet, können Sie das Kontextmenü verwenden, um den eingefügten Code im **Disassemblyfenster** zu suchen.  
  
### So zeigen Sie eingefügten Code an  
  
1.  Der Debugger muss sich im Unterbrechungsmodus befinden.  
  
2.  Positionieren Sie den Cursor im Quellcodefenster vor dem Attribut, dessen eingefügter Code angezeigt werden soll.  
  
3.  Klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü die Option **Gehe zu Disassembly** aus.  
  
     Wenn sich das Attribut in der Nähe des aktuellen Ausführungspunktes befindet, können Sie das **Disassemblyfenster** über das Menü **Debuggen** öffnen.  
  
### So zeigen Sie den Disassemblycode am aktuellen Ausführungspunkt an  
  
1.  Der Debugger muss sich im Unterbrechungsmodus befinden.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Disassembly**.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)