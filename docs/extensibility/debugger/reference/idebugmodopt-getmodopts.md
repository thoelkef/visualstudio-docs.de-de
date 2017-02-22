---
title: "IDebugModOpt::GetModOpts | Microsoft Docs"
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
  - "IDebugModOpt::GetModOpts"
  - "GetModOpts"
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste optionaler Modifizierer ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der zurückzugebenden Elemente.  
  
 `rgelt`  
 \[out\]  Gibt ein Array zurück, das die Optionen enthält.  
  
 `pceltFetched`  
 \[in, out\]  `rgelt` Anzahl der Elemente im Array zurückgegeben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)