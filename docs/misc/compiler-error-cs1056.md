---
title: "Compilerfehler CS1056 | Microsoft Docs"
ms.custom: ""
ms.date: "10/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1056"
ms.assetid: bf66d164-ab5b-4181-b93e-a1d29620b4d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1056
Unerwartetes Zeichen 'Zeichen'.  
  
 Der C\#\-Compiler hat ein unerwartetes Zeichen erkannt und kann das derzeit verarbeitete Token nicht identifizieren. Wenn der Compiler z. B. während der Verarbeitung eines Bezeichners ein Euro\-Zeichen erkennt, kann er den Bezeichner nicht klassifizieren, da ein Euro\-Zeichen nur innerhalb einer Zeichenfolge gültig wäre, und dem Compiler ist bekannt, dass er keine Zeichenfolge verarbeitet.