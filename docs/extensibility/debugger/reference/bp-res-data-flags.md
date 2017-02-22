---
title: "BP_RES_DATA_FLAGS | Microsoft Docs"
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
  - "BP_RES_DATA_FLAGS"
helpviewer_keywords: 
  - "BP_RES_DATA_FLAGS-enumeration"
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_RES_DATA_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, ob der Datenhaltepunkt in der Hardware emuliert oder implementiert wird.  
  
## Syntax  
  
```cpp#  
enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
typedef DWORD BP_RES_DATA_FLAGS;  
```  
  
```c#  
public enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
```  
  
## Mitglieder  
 BP\_RES\_DATA\_EMULATED  
 Gibt an, dass der Datenhaltepunkt emuliert wird.  
  
## Hinweise  
 Wird für den `dwFlags`\-Member der [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)