---
title: "&#39;&lt;Typname&gt;&#39; hat keine Typparameter und kann daher keine Typargumente haben. | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Typname&gt;&#39; hat keine Typparameter und kann daher keine Typargumente haben.
Eine Deklaration oder Zuweisungsanweisung umfasst eine [Of](/dotnet/visual-basic/language-reference/statements/of-clause)\-Klausel, wenn ein nicht generischer Typ aufgerufen wird.  
  
 Definitionsgemäß ist ein *generischer Typ* eine Klasse, Struktur, Schnittstelle, Prozedur oder ein Delegat, die bzw. der für Datentypen verwendet wird, die Sie über einen oder mehrere *Typparameter* angeben können. Wenn der Anwendungscode einen Typ aus diesem generischen Typ erstellt, stellt er für jeden Typparameter ein *Typargument* bereit. Im Rahmen der Typerstellung ersetzt jedes Typargument die einzelnen Vorkommen seines entsprechenden Typparameters im generierten Code.  
  
 Typparameter werden mit einer `Of`\-Klausel in Klammern definiert, und Typargumente werden mithilfe einer `Of`\-Klausel in Klammern bereitgestellt. Die `Of`\-Klausel wird nur bei generischen Typen verwendet.  
  
 Nicht generische Typen akzeptieren keine Typparameter, und Sie können beim Aufrufen eines solchen Typs keine Typargumente angeben.  
  
 **Fehler\-ID:** BC32045  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Typs, den Sie in der Deklaration oder Zuweisungsanweisung verwenden.  
  
2.  Wenn Sie einen nicht generischen Typ aufrufen, entfernen Sie die `Of`\-Klausel und die zugehörigen Klammern, sofern vorhanden. Entfernen Sie keine Klammern, die eine Standardargumentliste für eine Prozedur, einen Delegaten oder einen Klassenkonstruktor umgeben.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Gewusst wie: Verwenden einer generischen Klasse](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)