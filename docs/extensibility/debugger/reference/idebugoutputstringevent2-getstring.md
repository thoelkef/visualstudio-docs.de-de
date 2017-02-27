---
title: "IDebugOutputStringEvent2::GetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugOutputStringEvent2::GetString"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2::GetString"
ms.assetid: f059f8e0-ad44-49ac-ba90-73576ada5e06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugOutputStringEvent2::GetString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die anzeigbare Meldung.  
  
## Syntax  
  
```cpp#  
HRESULT GetString(   
   BSTR* pbstrString  
);  
```  
  
```c#  
int GetString(   
   out string pbstrString  
);  
```  
  
#### Parameter  
 `pbstrString`  
 \[out\]  Gibt die anzeigbare Meldung zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)