---
title: "&quot;Property Get/Let/Set&quot; werden nicht mehr unterst&#252;tzt. Verwenden Sie die neue Syntax zum Deklarieren von Eigenschaften | Microsoft Docs"
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
  - "vbc30808"
  - "bc30808"
helpviewer_keywords: 
  - "BC30808"
ms.assetid: c8a803eb-316d-4f73-b6ef-27a2914409f3
caps.latest.revision: 10
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Property Get/Let/Set&quot; werden nicht mehr unterst&#252;tzt. Verwenden Sie die neue Syntax zum Deklarieren von Eigenschaften
`Property Get/Let/Set` werden nicht mehr unterstützt. Verwenden Sie die neue `Property`\-Deklarationssyntax.  
  
 Die Syntax zum Deklarieren von Eigenschaften wurde geändert. Eigenschaften werden jetzt innerhalb von Blöcken definiert.  
  
 **Fehler\-ID:** BC30808  
  
### So beheben Sie diesen Fehler  
  
1.  Definieren Sie Eigenschaften in Codeblöcken, die mit dem `Property`\-Schlüsselwort beginnen. Beenden Sie Eigenschaften mit dem `End Property`\-Konstrukt.  
  
2.  Definieren Sie `Get`\-Eigenschaftenprozeduren innerhalb von Eigenschaftenblöcken mit dem `Get`\-Schlüsselwort. Beenden Sie `Get`\-Eigenschaftenprozeduren mit dem `End Get`\-Konstrukt.  
  
3.  Definieren Sie `Set`\-Eigenschaftenprozeduren innerhalb von Eigenschaftenblöcken mit dem `Set`\-Schlüsselwort. Beenden Sie `Set`\-Eigenschaftenprozeduren mit dem `End Set`\-Konstrukt.  
  
4.  Verwenden Sie `Set`\-Eigenschaftenprozeduren für alle Eigenschaftenzuweisungen.`Let`\-Eigenschaftenprozeduren werden nicht mehr benötigt und nicht mehr unterstützt.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Language Changes in Visual Basic](http://msdn.microsoft.com/de-de/a1be4461-a0e4-4a88-a32c-dcad41ed119a)