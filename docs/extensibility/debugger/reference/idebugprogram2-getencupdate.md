---
title: "IDebugProgram2::GetENCUpdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetENCUpdate"
helpviewer_keywords: 
  - "IDebugProgram2::GetENCUpdate"
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Bearbeitung ab und setzt Update \(Anlage\) für dieses Programm fortgesetzt.  Debuggen eines benutzerdefinierten Moduls gibt immer `E_NOTIMPL`zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```c#  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### Parameter  
 `ppUpdate`  
 \[out\]  Gibt eine interne Schnittstelle zurück, die verwendet werden kann, um das Programm zu aktualisieren.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein benutzerdefiniertes Modul sollte immer `E_NOTIMPL`Debug zurückgeben.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)