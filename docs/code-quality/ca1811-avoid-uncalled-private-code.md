---
title: "CA1811: Nicht aufgerufenen privaten Code vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811: Nicht aufgerufenen privaten Code vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Zu einem privaten oder internen Member \(auf Assemblyebene\) gibt es in der Assembly keine Aufrufer, er wird nicht durch die Common Language Runtime und nicht durch einen Delegaten aufgerufen.  Die folgenden Member werden von dieser Regel nicht überprüft:  
  
-   Explizite Schnittstellenmember.  
  
-   Statische Konstruktoren.  
  
-   Serialisierungskonstruktoren.  
  
-   Mit <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> markierte Methoden.  
  
-   Member, bei denen es sich um Überschreibungen handelt.  
  
## Regelbeschreibung  
 Diese Regel kann fälschlicherweise Verstöße melden, wenn es Einstiegspunkte gibt, die derzeit nicht durch die Regellogik identifiziert werden.  Auch gibt ein Compiler möglicherweise nicht aufrufbaren Code in eine Assembly aus.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht aufrufbaren Code, oder fügen Sie Code hinzu, der den Code aufruft.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  
  
## Verwandte Regeln  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)