---
title: "IDebugField::GetSize | Microsoft Docs"
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
  - "IDebugField::GetSize"
helpviewer_keywords: 
  - "IDebugField::GetSize-Methode"
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Größe des Felds in Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### Parameter  
 `pdwSize`  
 \[out\]  Gibt die Größe zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Alle Felder verfügen über einen Typ und alle Typen verfügen über eine Größe.  Beispielsweise verfügt ein Feld mit einem Typ Byte eine Größe von 1 Byte.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)