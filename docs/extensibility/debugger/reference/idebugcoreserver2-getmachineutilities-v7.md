---
title: "IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetMachineUtilities_V7"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetMachineUtilities_V7"
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Computer Hilfsprogramme für einen Server ab.  
  
> [!NOTE]
>  Diese Methode ist veraltet: Verwenden Sie keinen \([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer `E_NOTIMPL` zurück, wenn diese Methode aufgerufen wird\).  Er ist für historische Gründen beibehalten.  
  
## Syntax  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```c#  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### Parameter  
 `ppUtil`  
 \[out\]  Gibt eine `IDebugMDMUtil2_V7`\-Schnittstelle zurück, die die Computer die Informationen darstellt.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL`zurück, um anzugeben, dass die Methode nicht implementiert ist.  
  
## Hinweise  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer `E_NOTIMPL` zurück, wenn diese Methode aufgerufen wird.  
  
## Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)