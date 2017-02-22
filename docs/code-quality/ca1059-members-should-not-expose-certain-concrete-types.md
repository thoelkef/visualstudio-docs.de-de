---
title: "CA1059: Member sollten bestimmte konkrete Typen nicht verf&#252;gbar machen | Microsoft Docs"
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
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1059: Member sollten bestimmte konkrete Typen nicht verf&#252;gbar machen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer Member ist ein bestimmter konkreter Typ, oder er macht bestimmte konkrete Typen über einen seiner Parameter oder den Rückgabewert verfügbar.  Derzeit meldet diese Regel das Verfügbarmachen der folgenden konkreten Typen:  
  
-   Ein von <xref:System.Xml.XmlNode?displayProperty=fullName> abgeleiteter Typ.  
  
## Regelbeschreibung  
 Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann.  Damit der Member durchgängig verwendet werden kann, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle.  So kann der Member jeden Typ akzeptieren, der die Schnittstelle implementiert, oder dort verwendet werden, wo ein Typ erwartet wird, der die Schnittstelle implementiert.  
  
 In der folgenden Tabelle werden die verwendeten konkreten Typen und jeweils vorgeschlagenen Ersatzschnittstellen aufgelistet.  
  
|Konkreter Typ|Ersetzung|  
|-------------------|---------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Bei Verwenden der Schnittstelle wird der Member von einer bestimmten Implementierung einer XML\-Datenquelle entkoppelt.|  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den konkreten Typ in die vorgeschlagene Schnittstelle.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die bestimmte, vom konkreten Typ bereitgestellte Funktionalität erforderlich ist.  
  
## Verwandte Regeln  
 [CA1011: Basistypen als Parameter übergeben](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)