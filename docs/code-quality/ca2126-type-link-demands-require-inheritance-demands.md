---
title: "CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen | Microsoft Docs"
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
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
helpviewer_keywords: 
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2126: Typlinkaufrufe erfordern Vererbungsanforderungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher unversiegelter Typ wird mittels eines Linkaufrufs geschützt und weist eine überschreibbare Methode auf, aber weder der Typ noch die Methode werden durch eine Vererbungsanforderung geschützt.  
  
## Regelbeschreibung  
 Für einen Linkaufruf, der für eine Methode oder den zugehörigen deklarierenden Typ durchgeführt wird, muss der unmittelbare Aufrufer der Methode über die angegebene Berechtigung verfügen.  Für eine Vererbungsanforderung, die für eine Methode durchgeführt wird, muss eine überschreibende Methode die angegebene Berechtigung aufweisen.  Für eine Vererbungsanforderung, die für einen Typ durchgeführt wird, muss eine Ableitungsklasse die angegebene Berechtigung aufweisen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, schützen Sie den Typ oder die Methode mit einer Vererbungsanforderung, für die dieselbe Berechtigung erforderlich ist wie für den Linkaufruf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-cs[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## Verwandte Regeln  
 [CA2108: Deklarative Sicherheit auf Werttypen überprüfen](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Demands](http://msdn.microsoft.com/de-de/e5283e28-2366-4519-b27d-ef5c1ddc1f48)