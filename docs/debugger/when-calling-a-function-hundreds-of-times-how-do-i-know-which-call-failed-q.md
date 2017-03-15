---
title: "Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr h&#228;ufig aufgerufen wird? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Haltepunkte, Problembehandlung"
  - "Bedingte Haltepunkte"
  - "Fehler [Debugger], Ermitteln des fehlgeschlagenen Funktionsaufrufs"
  - "Fehler [Debugger], Funktionsaufrufe"
  - "Fehler [Visual Studio], Funktionsaufrufe"
  - "Fehler"
  - "Funktionsaufrufe, Fehler"
  - "Funktionen [Debugger]"
  - "Trefferanzahlen"
  - "Positionshaltepunkt-Aufruffehler"
  - "Anzahl der Durchläufe"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr h&#228;ufig aufgerufen wird?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Problembeschreibung  
 Das Programm schlägt bei einem Aufruf einer bestimmten Funktion mit dem Namen `CnvtV` fehl.  Zuvor hat das Programm die Funktion jedoch mehrere Hundert Male aufgerufen.  Wenn ein Positionshaltepunkt für `CnvtV` festgelegt wird, hält das Programm bei jedem Aufruf der Funktion an, was nicht beabsichtigt ist.  Da nicht bekannt ist, welche Bedingungen den fehlschlagenden Aufruf verursachen, kann kein bedingter Haltepunkt festgelegt werden.  Welche Möglichkeiten gibt es?  
  
## Lösung  
 Mithilfe des Felds **Trefferanzahl** können Sie den Haltepunkt für die Funktion auf einen hohen Wert festlegen, der niemals erreicht wird.  Da Sie davon ausgehen, dass die `CnvtV`\-Funktion einige Hundert Male aufgerufen wird, könnten Sie **Trefferanzahl** auf einen Wert von mindestens 1000 festlegen.  Führen Sie dann das Programm aus, und warten Sie, bis der Aufruf fehlschlägt.  Sobald dies der Fall ist, öffnen Sie das Fenster "Haltepunkte" und überprüfen die Haltepunktliste.  Der für `CnvtV` festgelegte Haltepunkt wird, gefolgt von der Trefferanzahl und der Anzahl der noch verbleibenden Iterationen, angezeigt:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Jetzt wissen Sie, dass die Funktion bei Aufruf Nr. 101 fehlgeschlagen ist.  Wenn Sie nun den Haltepunkt auf eine Trefferanzahl von 101 zurücksetzen und das Programm erneut ausführen, hält es an dem `CnvtV`\-Aufruf an, der zuvor den Fehler verursacht hat.  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/de-de/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)