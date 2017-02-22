---
title: "IDebugAlias2::GetAppDomainId | Microsoft Docs"
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
  - "GetAppDomainId"
  - "IDebugAlias2::GetAppDomainId"
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bezeichner der Anwendungsdomäne ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```c#  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### Parameter  
 `pappDomainId`  
 \[out\]  Gibt den Bezeichner der Anwendungsdomäne zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Bezeichner der Anwendungsdomäne geändert wird, sobald die Anwendung neu gestartet wird und eine neue Anwendungsdomäne erstellt wurde.  
  
## Siehe auch  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)