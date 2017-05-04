---
title: "IActiveScriptSiteUIControl::GetUIBehavior-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior-Methode
Ruft [SCRIPTUICHANDLING\-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md) ab, das die Methode darstellt, die ein UI\-Steuerelement behandelt werden soll.  
  
## Syntax  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### Parameter  
 `UicItem`  
 Der Typ des Steuerelements.  
  
 `pUicHandling`  
 Die Methode sollte das Steuerelement behandelt werden.