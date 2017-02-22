---
title: "IDebugPortPicker::SetSite | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker::SetSite"
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Dienstanbieter festgelegt.  
  
## Syntax  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```c#  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### Parameter  
 `pSP`  
 \[in\]  Verweis auf die Schnittstelle des Dienstanbieters.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird aufgerufen, bevor andere Methoden aufgerufen werden.  
  
## Siehe auch  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)