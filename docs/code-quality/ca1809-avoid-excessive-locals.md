---
title: "CA1809: &#220;berm&#228;&#223;ige lokale Variablen vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1809: &#220;berm&#228;&#223;ige lokale Variablen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Member enthält mehr als 64 lokale Variablen, von denen einige möglicherweise vom Compiler generiert wurden.  
  
## Regelbeschreibung  
 Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als *Registrierung* des Werts bezeichnet.  Die Common Language Runtime zieht bis zu 64 lokale Variablen für die Registrierung in Betracht.  Variablen, die nicht registriert werden, werden auf den Stapel verschoben und müssen vor der Bearbeitung in ein Register verschoben werden.  Um die Möglichkeit offen zu halten, dass alle lokalen Variablen registriert werden, beschränken Sie die Anzahl der lokalen Variablen auf 64.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Implementierung so um, dass nicht mehr als 64 lokale Variablen verwendet werden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, bzw. die Regel kann deaktiviert werden, wenn das Leistungsverhalten nicht von Belang ist.  
  
## Verwandte Regeln  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)