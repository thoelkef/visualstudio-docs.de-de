---
title: "IDebugDefaultPort2::QueryIsLocal | Microsoft Docs"
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
  - "IDebugDefaultPort2::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugDefaultPort2::QueryIsLocal"
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode bestimmt, ob der Port auf dem lokalen Computer befindet.  
  
## Syntax  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```c#  
int QueryIsLocal();  
```  
  
## Rückgabewert  
 Gibt `S_OK` zurück, wenn dieser Port \(lokal auf demselben Computer wie der Aufrufer\) oder `S_FALSE` ist, wenn der Anschluss auf einem anderen Computer befindet.  
  
## Siehe auch  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)