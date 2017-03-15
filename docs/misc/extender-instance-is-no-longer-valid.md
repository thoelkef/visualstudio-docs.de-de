---
title: "Extender instance is no longer valid. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTINVALID"
ms.assetid: 6361ba35-f2c5-4024-9362-46d7d9daf651
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender instance is no longer valid.
Die Extenderinstanz konnte nicht erfolgreich erstellt werden oder wurde beschädigt.  
  
### So beheben Sie diesen Fehler  
  
1.  Rufen Sie erneut die Extenderinstanz vom Extendee\-Objekt ab.  
  
     \- oder \-  
  
     Rufen Sie erneut die Extenderinstanz ab, indem Sie DTE.ObjectExtenders.GetExtender\(\) aufrufen.  
  
## Siehe auch  
 <xref:EnvDTE.ObjectExtenders>   
 <xref:EnvDTE.ObjectExtenders.GetExtender%2A>