---
title: "CA1020: Namespaces mit wenigen Typen vermeiden | Microsoft Docs"
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
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1020: Namespaces mit wenigen Typen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein anderer Namespace als der globale Namespace enthält weniger als fünf Typen.  
  
## Regelbeschreibung  
 Stellen Sie sicher, dass jeder der Namespaces logisch organisiert ist und dass es einen zulässigen Grund dafür gibt, Typen in einen wenig gefüllten Namespace einzufügen.  Namespaces sollten Typen enthalten, die in den meisten Szenarien zusammen verwendet werden.  Wenn die Anwendungen sich gegenseitig ausschließen, sollten sich die Typen in separaten Namespaces befinden.  Der <xref:System.Web.UI>\-Namespace enthält z. B. Typen, die in Webanwendungen verwendet werden, während der <xref:System.Windows.Forms>\-Namespace Typen enthält, die in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]\-basierten Anwendungen verwendet werden.  Obwohl beide Namespaces Typen haben, die Aspekte der Benutzeroberfläche steuern, sind diese Typen nicht zur Verwendung in der gleichen Anwendung vorgesehen.  Daher sind sie in separaten Namespaces.  Eine sorgfältige Organisation der Namespaces kann auch hilfreich sein, da sich Features dadurch leichter auffinden lassen.  Bibliotheksconsumer sollten durch Prüfung der Namespacehierarchie in der Lage sein, die Typen zu finden, die ein Feature implementieren.  
  
> [!NOTE]
>  Zur Einhaltung dieser Richtlinie sollten Entwurfszeittypen und Berechtigungen nicht in andere Namespaces integriert werden.  Diese Typen gehören in ihre eigenen Namespaces unterhalb des Hauptnamespaces, und die Namespaces sollten auf `.Design` bzw. `.Permissions` enden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, versuchen Sie, Namespaces, die nur wenig Typen enthalten, zu einem einzigen Namespace zusammenzufassen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Namespace keine Typen enthält, die mit den Typen in den anderen Namespaces verwendet werden.