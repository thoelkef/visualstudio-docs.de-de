---
title: "Typparameter k&#246;nnen in dieser Deklaration nicht angegeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32065"
  - "bc32065"
helpviewer_keywords: 
  - "BC32065"
ms.assetid: 94cfe3de-74fd-4a2c-9246-ec4a05b73d55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typparameter k&#246;nnen in dieser Deklaration nicht angegeben werden.
Ein Programmierelement ist mit einer Typparameterliste deklariert, aber das Programmierelement ist nicht für einen generischen Typ qualifiziert.  
  
 Zu den Programmierelementen, die nicht als Generika in Frage kommen, gehören Eigenschaften, Operatoren, Ereignisse und Konstruktoren. Das Deklarieren eines dieser Elemente mit einer Typparameterliste führt zu diesem Fehler.  
  
 **Fehler\-ID:** BC32065  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Of`\-Schlüsselwort und die Typparameter aus der Deklaration.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)