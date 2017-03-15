---
title: "&quot;&lt;Schl&#252;sselwort&gt;&quot; ist nur innerhalb einer Klasse g&#252;ltig | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Schl&#252;sselwort&gt;&quot; ist nur innerhalb einer Klasse g&#252;ltig
Ein Schlüsselwort in Bezug auf Klassen, z. B. `Me` oder `MyClass`, wird außerhalb einer Klassendefinition verwendet.  
  
 **Fehler\-ID:** BC32002  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Code, in dem das Schlüsselwort verwendet wird, Klasseninstanzen betrifft, verschieben Sie es in eine Klassenimplementierung.  
  
-   Wenn der Code, in dem das Schlüsselwort verwendet wird, nicht für Klassen gilt, entfernen Sie das ungültige Schlüsselwort.  
  
## Siehe auch  
 [Me](http://msdn.microsoft.com/de-de/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- löschen](http://msdn.microsoft.com/de-de/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)