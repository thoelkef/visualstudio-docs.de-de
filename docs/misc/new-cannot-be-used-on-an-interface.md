---
title: "„New“ kann nicht f&#252;r eine Schnittstelle verwendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „New“ kann nicht f&#252;r eine Schnittstelle verwendet werden.
Eine [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement) verwendet eine [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)\-Klausel, wenn eine Variable als Schnittstellentyp deklariert wird.  
  
 Obwohl eine Schnittstelle ein Verweistyp ist, können Sie keine Instanz von ihr erstellen. Sie können `New` nur zum Erstellen einer Instanz einer Klasse oder einer Struktur verwenden.  
  
 **Fehler\-ID:** BC30375  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn die Variable einen Schnittstellentyp aufweisen soll, entfernen Sie das `New`\-Schlüsselwort.  
  
2.  Wenn die Variable auf eine Instanz verweisen soll, deklarieren Sie sie als Klassen\- oder Strukturtyp. Behalten Sie das `New`\-Schlüsselwort bei, um eine Instanz zu erstellen.  
  
## Siehe auch  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)