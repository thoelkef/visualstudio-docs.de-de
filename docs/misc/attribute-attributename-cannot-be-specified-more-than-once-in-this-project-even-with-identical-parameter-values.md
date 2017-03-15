---
title: "Das Attribut &quot;&lt;Attributname&gt;&quot; kann in diesem Projekt nicht mehrmals angegeben werden, selbst wenn die Parameterwerte identisch sind. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Attribut &quot;&lt;Attributname&gt;&quot; kann in diesem Projekt nicht mehrmals angegeben werden, selbst wenn die Parameterwerte identisch sind.
Ein benutzerdefiniertes Attribut ist für dasselbe Programmierelement mehrmals angegeben. <xref:System.AttributeUsageAttribute> wird jedoch auf das benutzerdefinierte Attribut angewendet, und die <xref:System.AttributeUsageAttribute.AllowMultiple%2A>\-Eigenschaft wird auf `False` festgelegt.<xref:System.AttributeUsageAttribute.AllowMultiple%2A> steuert, ob das Attribut mehrmals verwendet werden kann.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC41000  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die zusätzliche Angabe des benutzerdefinierten Attributs, oder legen Sie im darauf angewendeten <xref:System.AttributeUsageAttribute><xref:System.AttributeUsageAttribute.AllowMultiple%2A> auf `True` fest.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)