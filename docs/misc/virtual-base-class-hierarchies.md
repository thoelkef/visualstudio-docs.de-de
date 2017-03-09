---
title: "Hierarchien der virtuellen Basisklassen | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Klassen [C++], virtuelle Basisklassen"
  - "Klassenhierarchien, virtuelle Basisklassen"
  - "abgeleitete Klassen, Überlegungen zur Klassenhierarchie"
  - "virtuelle Funktionen, die in Hierarchien der virtuellen Basisklassen"
  - "virtuelle Basisklassen"
  - "virtuelle Basisklassen Hierarchien"
  - "Hierarchien, virtuelle Basisklasse"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Hierarchien der virtuellen Basisklassen
Einige Klassenhierarchien sind zwar umfangreich, haben aber vieles gemeinsam. Der gemeinsame Code wird in einer Basisklasse implementiert, während der spezifische Code in abgeleiteten Klassen implementiert wird.  
  
 Es ist wichtig, für die Basisklassen ein Protokoll festzulegen, wodurch den abgeleiteten Klassen maximale Funktionalität gewährleistet werden kann. Diese Protokolle werden im Allgemeinen mit virtuellen Funktionen implementiert. In einigen Fällen stellt die Basisklasse eine Standardimplementierung für solche Funktionen bereit. In einer Klassenhierarchie wie der Hierarchie `Document` in der Abbildung mit einem Beispiel eines gerichteten azyklischen Diagramms \(siehe [Single Inheritance](/visual-cpp/cpp/single-inheritance)\) sind zwei nützliche Funktionen `Identify` und `WhereIs`.  
  
 Wenn sie aufgerufen wird, gibt die Funktion `Identify` die richtige ID zurück, passend zur Art des Dokuments: Für `Book` muss ein Funktionsaufruf wie `doc->Identify()` die ISBN\-Nummer zurückgeben. Für `HelpFile` passen jedoch ein Produktname und die Revisionsnummer wahrscheinlich besser. Entsprechend sollte `WhereIs` eine Zeile und eine Plattform für `Book` zurückgeben, aber für `HelpFile` sollte ein Speicherort auf einem Datenträger zurückgegeben werden, zum Beispiel ein Verzeichnis und ein Dateiname.  
  
 Es ist wichtig, dass alle Implementierungen der `Identify`\- und `WhereIs`\-Funktionen die gleiche Art von Informationen zurückgeben. In diesem Fall ist eine Zeichenfolge geeignet.  
  
 Diese Funktionen werden als virtuelle Funktionen implementiert und anschließend mithilfe eines Zeigers auf eine Basisklasse aufgerufen. Die Bindung an den eigentlichen Code erfolgt zur Laufzeit, wobei die richtige `Identify`\- oder `WhereIs`\-Funktion ausgewählt wird.  
  
## Siehe auch  
 [Übersicht über abgeleitete Klassen](../misc/overview-of-derived-classes.md)