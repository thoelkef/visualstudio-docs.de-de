---
title: "IDebugModule3::SetJustMyCodeState | Microsoft Docs"
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
  - "IDebugModule3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugModule3::SetJustMyCodeState"
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Markiert das Modul als Benutzercode oder nicht.  
  
## Syntax  
  
```cpp#  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### Parameter  
 `fIsUserCode`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), wenn das Modul als Benutzercode behandelt wird,`FALSE`\(null\), falls nicht.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)