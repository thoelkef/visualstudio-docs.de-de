---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
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
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode explizit wird Bearbeiten und Fortfahren deaktiviert in diesem Prozess fort \(und Alle Programme, die sie enthält.\)  Ein benutzerdefinierter Port lieferant sollte immer `E_NOTIMPL`zurückgeben.  
  
## Syntax  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### Parameter  
 `reason`  
 \[in\]  Ein Wert aus der [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)\-Enumeration.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
> [!NOTE]
>  Ein benutzerdefinierter Port lieferant sollte immer `E_NOTIMPL`zurückgeben.  
  
## Hinweise  
 Einmal Bearbeiten und Fortfahren wird für einen Prozess erneut aktiviert werden, es kann nur deaktiviert werden, indem dem Prozess neu gestartet wird.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)