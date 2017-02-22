---
title: "IDebugProgram2::GetProgramId | Microsoft Docs"
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
  - "IDebugProgram2::GetProgramId"
helpviewer_keywords: 
  - "IDebugProgram2::GetProgramId"
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine GUID für dieses Programm ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### Parameter  
 `pguidProgramId`  
 \[out\]  Gibt `GUID` für dieses Programm zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Modul \(Debug\) muss DE den Programmbezeichner zurückgeben, der ursprünglich zum [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode übergeben wird.  Dadurch kann die Identifikation des Programms über Debugger Komponenten.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)