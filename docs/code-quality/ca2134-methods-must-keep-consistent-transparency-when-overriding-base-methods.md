---
title: "CA2134: Methoden m&#252;ssen beim &#220;berschreiben von Basismethoden eine konsistente Transparenz wahren | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134: Methoden m&#252;ssen beim &#220;berschreiben von Basismethoden eine konsistente Transparenz wahren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Diese Regel wird ausgelöst, wenn eine Methode, die mit dem <xref:System.Security.SecurityCriticalAttribute>\-Objekt markiert ist, eine Methode überschreibt, die transparent oder mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Objekt markiert ist.  Die Regel wird auch ausgelöst, wenn eine Methode, die transparent ist oder mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Objekt markiert ist, eine Methode überschreibt, die transparent oder mit dem <xref:System.Security.SecurityCriticalAttribute>\-Objekt markiert ist.  
  
 Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird.  
  
## Regelbeschreibung  
 Diese Regel wird für Versuche ausgelöst, die Sicherheitsbarrierefreiheit einer Methode weiter oben in der Vererbungskette zu ändern.  Wenn eine virtuelle Methode in einer Basisklasse z. B. transparent oder sicherheitsgeschützt ist, dann muss die abgeleitete Klasse sie mit einer transparenten oder sicherheitsgeschützten Methode überschreiben.  Umgekehrt, wenn das virtuelle Element sicherheitskritisch ist, muss die abgeleitete Klasse es mit einer sicherheitskritischen Methode überschreiben.  Die gleiche Regel gilt für das Implementieren von Schnittstellenmethoden.  
  
 Transparenzregeln werden erzwungen, wenn der Code JIT und nicht zur Laufzeit kompiliert wird, sodass die Transparenzberechnung keine dynamischen Typinformationen aufweist.  Daher muss das Ergebnis der Transparenzberechnung ausschließlich anhand der statischen Typen bestimmt werden können, die JIT\-kompiliert werden, und zwar unabhängig vom dynamischen Typ.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, ändern Sie die Transparenz der Methode, die eine virtuelle Methode überschreibt oder eine Schnittstelle implementiert, damit sie mit der Transparenz der virtuellen Methode oder der Schnittstellenmethode übereinstimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Verstöße gegen diese Regel führen zu einer Laufzeit <xref:System.TypeLoadException> für Assemblys, die Transparenz der Ebene 2 verwenden.  
  
## Beispiele  
  
### Code  
 [!code-cs[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## Siehe auch  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)