---
title: "IDebugEngine2::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Registrierungsstamm für das Debugmodul fest \(DE\).  
  
## Syntax  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### Parameter  
 `pszRegistryRoot`  
 \[in\]  Der zu verwendende Registrierungsstamm.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ermöglicht [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , um einen alternativen Registrierungsstamm anzugeben, der verwendet werden soll, um DE Registrierungseinstellungen zu erhalten. z. B. „HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 8.0Exp“.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)