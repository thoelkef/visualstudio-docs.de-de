---
title: "IDebugPortSupplier2::AddPort | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::AddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::AddPort"
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt einen Port hinzufügen.  
  
## Syntax  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```c#  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### Parameter  
 `pRequest`  
 \[in\]  Ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)\-Objekt, das den Anschluss beschrieben, die hinzugefügt werden soll.  
  
 `ppPort`  
 \[out\]  Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt zurück, das den Anschluss darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode stellt den angeforderten Anschluss erstellen und sie der internen Liste des Anschlusslieferanten aktiver Ports.  Die [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)\-Methode zuerst aufgerufen werden kann, um mögliche Verzögerungen zeitaufwändige zu vermeiden.  
  
## Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)