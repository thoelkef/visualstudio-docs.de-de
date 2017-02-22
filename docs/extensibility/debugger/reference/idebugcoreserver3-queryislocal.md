---
title: "IDebugCoreServer3::QueryIsLocal | Microsoft Docs"
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
  - "IDebugCoreServer3::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugCoreServer3::QueryIsLocal"
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob der Server den Aufrufer lokal ist.  
  
## Syntax  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```c#  
int QueryIsLocal();  
```  
  
## Rückgabewert  
 Gibt `S_OK` zurück, um den Server anzugeben ist lokal.  Gibt `S_FALSE` zurück, wenn der Server als eine Instanz von msvsmon.exe ausführt, die normalerweise für das Remotedebuggen verwendet wird.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)