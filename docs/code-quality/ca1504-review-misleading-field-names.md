---
title: "CA1504: Irref&#252;hrende Feldnamen &#252;berpr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1504: Irref&#252;hrende Feldnamen &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Der Name eines Instanzfelds beginnt mit "s\_", oder der Name eines `static`\-Felds \(`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) beginnt mit "m\_."  
  
## Regelbeschreibung  
 Feldnamen, die mit "s\_" beginnen, werden von vielen Benutzern mit statischen Daten in Verbindung gebracht.  Entsprechend werden Feldnamen, die mit "m\_" beginnen, Instanz\(member\)daten zugeordnet.  Damit Code einfacher zu verwalten ist, sollten bei Namen allgemein verwendete Konventionen befolgt werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie das Feld mit dem entsprechenden Präfix umbenennen.  Alternativ passen Sie das Feld an das aktuelle Suffix an, indem Sie den `static`\-Modifizierer hinzufügen oder entfernen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.