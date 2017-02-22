---
title: "IDebugProcess3::GetENCAvailableState | Microsoft Docs"
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
  - "IDebugProcess3::GetENCAvailableState"
helpviewer_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft den aktuellen Bearbeitungsvorgang ab und setzt Zustand des Prozesses fort.  Ein benutzerdefinierter Port lieferant sollte immer `E_NOTIMPL`zurückgeben.  
  
## Syntax  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```c#  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### Parameter  
 `pReason`  
 \[out\]  Ein Wert aus der [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)\-Enumeration.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
> [!NOTE]
>  Ein benutzerdefinierter Port lieferant sollte immer `E_NOTIMPL`zurückgeben.  
  
## Hinweise  
 Dieser Zustand kann durch [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)beeinflusst werden.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)