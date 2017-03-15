---
title: "Ereignisse in einem Modul k&#246;nnen nicht als &#39;&lt;spezifizierer&gt;&#39; deklariert werden | Microsoft Docs"
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
  - "bc30434"
  - "vbc30434"
helpviewer_keywords: 
  - "BC30434"
ms.assetid: ac6a63e3-89a6-4fbb-ade1-4fa033252379
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ereignisse in einem Modul k&#246;nnen nicht als &#39;&lt;spezifizierer&gt;&#39; deklariert werden
Sie haben einen Spezifizierer verwendet, der für ein Ereignis innerhalb einer `Module`\-Anweisung nicht gültig ist. Module können nie instanziiert werden, unterstützen keine Vererbung und können keine Schnittstellen implementieren.  
  
 **Fehler\-ID:** BC30434  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Spezifizierer.  
  
## Siehe auch  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)