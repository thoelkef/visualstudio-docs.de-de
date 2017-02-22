---
title: "CA1030: Nach M&#246;glichkeit Ereignisse verwenden | Microsoft Docs"
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
  - "UseEventsWhereAppropriate"
  - "CA1030"
helpviewer_keywords: 
  - "CA1030"
  - "UseEventsWhereAppropriate"
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1030: Nach M&#246;glichkeit Ereignisse verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher, geschützter oder privater Methodenname beginnt mit einer der folgenden Zeichenfolgen:  
  
-   AddOn  
  
-   RemoveOn  
  
-   Fire  
  
-   Raise  
  
## Regelbeschreibung  
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden.  Ereignisse entsprechen dem Entwurfsmuster Beobachter oder Veröffentlichen\-Abonnieren. Sie werden benutzt, wenn andere Objekte über eine Zustandsänderung in einem Objekt informiert werden müssen.  Wenn eine Methode auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden.  Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.  
  
 Einige gängige Beispiele für Ereignisse finden sich in Benutzeroberflächenanwendungen, in denen eine Benutzeraktion, z. B. das Klicken auf eine Schaltfläche, die Ausführung eines bestimmtes Codesegments bewirkt.  Das Ereignismodell von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ist nicht auf Benutzeroberflächen beschränkt. Es sollte überall dort verwendet werden, wo ein oder mehrere Objekte über Zustandsänderungen informiert werden müssen.  
  
## Behandeln von Verstößen  
 Wenn die Methode aufgerufen wird, sobald sich der Zustand eines Objekts ändert, sollten Sie in Erwägung ziehen, den Entwurf zu ändern und das Ereignismodell von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zu verwenden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn sich das Ereignismodell von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nicht für die Methode eignet.