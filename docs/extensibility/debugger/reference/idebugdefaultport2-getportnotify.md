---
title: "IDebugDefaultPort2::GetPortNotify | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::GetPortNotify"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetPortNotify"
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)\-Schnittstelle für diesen Port ab.  
  
## Syntax  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```c#  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### Parameter  
 `ppPortNotify`  
 \[out\]  Ein [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)\-Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Normalerweise wird die `QueryInterface`\-Methode, um dem Objekt aufgerufen, das die Schnittstelle implementiert [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) zum Abrufen einer [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)\-Schnittstelle.  Es gibt jedoch Umstände, unter denen die gewünschte Schnittstelle für ein anderes Objekt implementiert wird.  Diese Methode blendet diese Bedingungen aus und gibt die `IDebugPortNotify2`\-Schnittstelle aus dem entsprechendsten Objekt zurück.  
  
## Siehe auch  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)