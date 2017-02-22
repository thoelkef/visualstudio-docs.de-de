---
title: "IDebugProperty2::GetReference | Microsoft Docs"
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
  - "IDebugProperty2::GetReference"
helpviewer_keywords: 
  - "IDebugProperty2::GetReference-Methode"
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt einen Verweis auf den Wert der Eigenschaft zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```c#  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### Parameter  
 `ppRererence`  
 \[out\]  Gibt ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekt zurück, das einen Verweis auf den Wert der Eigenschaft darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode, i. d. R. `E_NOTIMPL` oder `E_GETREFERENCE_NO_REFERENCE`zurück.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)