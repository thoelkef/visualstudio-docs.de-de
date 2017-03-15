---
title: "CA1051: Sichtbare Instanzfelder nicht deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: Sichtbare Instanzfelder nicht deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer Typ verfügt über ein extern sichtbares Instanzenfeld.  
  
## Regelbeschreibung  
 Ein Feld sollte primär als Implementierungsdetail verwendet werden.  Felder sollten `private` oder `internal` sein und durch Verwendung von Eigenschaften verfügbar gemacht werden.  Auf eine Eigenschaft kann genau so einfach wie auf ein Feld zugegriffen werden. Der Code in den Accessoren einer Eigenschaft kann sich ändern, wenn die Funktionen des Typs erweitert werden. Änderungen, die die Lauffähigkeit der Anwendung beeinträchtigen, werden nicht vorgenommen.  Eigenschaften, die lediglich den Wert eines privaten oder internen Felds zurückgeben, sind optimiert, sodass ihre Leistung derjenigen des Zugriffs auf ein Feld entspricht. Die Verwendung extern sichtbarer Felder bedeutet nur einen geringen Leistungszuwachs gegenüber der Verwendung von Eigenschaften.  
  
 Extern sichtbar bezieht sich auf die Zugriffsebenen `public`, `protected` und `protected internal` \(`Public`, `Protected` und `Protected Friend` in Visual Basic\).  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie das Feld als `private` oder `internal`, und stellen Sie es mithilfe einer extern sichtbaren Eigenschaft zur Verfügung.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Extern sichtbare Felder bieten keine Vorteile, die Eigenschaften nicht zur Verfügung stehen.  Zusätzlich können öffentliche Felder nicht durch [Link Demands](../Topic/Link%20Demands.md) geschützt werden.  Siehe [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht \(`BadPublicInstanceFields`\), der gegen diese Regel verstößt.  `GoodPublicInstanceFields` zeigt den korrigierten Code.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Verwandte Regeln  
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## Siehe auch  
 [Link Demands](../Topic/Link%20Demands.md)