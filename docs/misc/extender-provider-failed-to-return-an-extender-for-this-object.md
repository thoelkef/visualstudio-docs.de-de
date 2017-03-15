---
title: "Extender Provider failed to return an Extender for this object. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_EXTCANTEXTEND"
ms.assetid: 96702669-b720-4076-91b6-bb29ec830a65
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider failed to return an Extender for this object.
Es konnte kein Extender zurückgegeben werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Fähigkeit der Implementierungen von IExtenderProvider::CanExtend\(\) und IExtenderProvider::GetExtender\(\) bezüglich der Rückgabe eines gültigen Extender\-Objekts.  
  
## Siehe auch  
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>