---
title: "Auf die implementierende Klasse &#39;&lt;ZugrundeliegenderKlassenname&gt;&#39; f&#252;r die Schnittstelle &#39;&lt;Schnittstellenname&gt;&#39; kann in diesem Kontext nicht zugegriffen werden, weil es sich um &#39;&lt;Zugriffsebene&gt;&#39; handelt. | Microsoft Docs"
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
  - "BC31109"
  - "vbc31109"
helpviewer_keywords: 
  - "BC31109"
ms.assetid: ab2a3bc3-b875-476f-b601-3e736ad2677e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf die implementierende Klasse &#39;&lt;ZugrundeliegenderKlassenname&gt;&#39; f&#252;r die Schnittstelle &#39;&lt;Schnittstellenname&gt;&#39; kann in diesem Kontext nicht zugegriffen werden, weil es sich um &#39;&lt;Zugriffsebene&gt;&#39; handelt.
Eine Schnittstelle wird mit dem <xref:System.Runtime.InteropServices.CoClassAttribute> deklariert, das eine zugrunde liegende Klasse angibt. Diese Klasse verfügt aber über eine Zugriffsebene, die verhindert, dass der verwendende Code darauf zugreifen kann.  
  
 Wenn das <xref:System.Runtime.InteropServices.CoClassAttribute> auf eine Schnittstelle angewendet wird, wird eine zugrunde liegenden Klasse der Schnittstelle zugeordnet. Dies ermöglicht es dem Code, ein Objekt direkt aus der Schnittstelle mithilfe einer `New`\-Klausel zu erstellen.  
  
 Wenn der Code, der die `New`\-Klausel verwendet, keinen Zugriff auf die zugrunde liegende Klasse besitzt \(weil die Klasse z. B. `Private` ist\), generiert der Compiler diesen Fehler.  
  
 **Fehler\-ID:** BC31109  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie über Quellcodeverwaltung für die zugrunde liegende Klasse verfügen, passen sie ihre Zugriffsebene einfach so an, dass der verwendende Code darauf zugreifen kann.  
  
2.  Wenn Sie die Zugriffsebene der zugrunde liegenden Klasse aus bestimmten Gründen nicht ändern können, entfernen Sie die `New`\-Klausel. Ein Objekt kann nicht direkt aus dieser Schnittstelle erstellt werden.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.CoClassAttribute>   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)