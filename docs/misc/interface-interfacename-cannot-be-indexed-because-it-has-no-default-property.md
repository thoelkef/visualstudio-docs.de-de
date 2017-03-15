---
title: "Schnittstelle &lt;Schnittstellenname&gt; kann nicht indiziert werden, da keine Standardeigenschaft vorhanden ist. | Microsoft Docs"
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
  - "bc30547"
  - "vbc30547"
helpviewer_keywords: 
  - "BC30547"
ms.assetid: d9d83868-5e81-4ec5-878e-2303489d8f2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Schnittstelle &lt;Schnittstellenname&gt; kann nicht indiziert werden, da keine Standardeigenschaft vorhanden ist.
Indexausdrücke müssen einen Wert, dessen Typ ein Array ist, einen Wert, dessen Typ einen Satz von überladenen Standardeigenschaften besitzt, oder eine Gruppe von überladenen Eigenschaften erzeugen. Eine Schnittstelle kann nur eine Standardmethode oder \-eigenschaft besitzen. Dies bedeutet, dass sie entweder eine Schnittstelle mit einer Standardmethode oder \-eigenschaft erben kann, oder dass ihr Definitionsblock eine Methode oder Eigenschaft enthalten kann, die als Standard markiert ist.  
  
 **Fehler\-ID:** BC30547  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie eine Standardeigenschaft in der Schnittstelle an.  
  
## Siehe auch  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)