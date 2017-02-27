---
title: "CA2212: ServicedComponents nicht mit WebMethod markieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2212: ServicedComponents nicht mit WebMethod markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode in einem Typ, der von <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> erbt, wird mit <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> markiert.  
  
## Regelbeschreibung  
 <xref:System.Web.Services.WebMethodAttribute> wird auf Methoden in einem XML\-Webdienst angewendet, die mit ASP.NET erstellt wurden. Dadurch kann die Methode durch Remotewebclients aufgerufen werden.  Die Methode und die Klasse müssen öffentlich sein und in einer ASP.NET\-Webanwendung ausgeführt werden.  <xref:System.EnterpriseServices.ServicedComponent>\-Typen werden von COM\+\-Anwendungen gehostet und können COM\+\-Dienste verwenden.  <xref:System.Web.Services.WebMethodAttribute> wird nicht für <xref:System.EnterpriseServices.ServicedComponent>\-Typen übernommen, da sie nicht für die gleichen Szenarios vorgesehen sind.  Insbesondere bewirkt das Hinzufügen des Attributs zur <xref:System.EnterpriseServices.ServicedComponent>\-Methode nicht, dass die Methode von Remotewebclients aufgerufen werden kann.  Da das Verhalten von <xref:System.Web.Services.WebMethodAttribute> und einer <xref:System.EnterpriseServices.ServicedComponent>\-Methode sowie deren Anforderungen an den Kontext sowie den Transaktionsablauf zu Konflikten führen, ist das Verhalten der Methode in bestimmten Szenarien fehlerhaft.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Attribut aus der <xref:System.EnterpriseServices.ServicedComponent>\-Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Es gibt keine Szenarien, in denen eine Kombination dieser Elemente richtig ist.  
  
## Siehe auch  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>