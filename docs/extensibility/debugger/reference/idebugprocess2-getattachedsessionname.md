---
title: "IDebugProcess2::GetAttachedSessionName | Microsoft Docs"
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
  - "IDebugProcess2::GetAttachedSessionName"
helpviewer_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen der Sitzung ab, die diesen Prozess gedebuggt wird.  Ein IDE kann diese Informationen für einen Benutzer angezeigt, der einen bestimmten Prozess auf einem bestimmten Computer gedebuggt.  
  
> [!NOTE]
>  Diese Methode ist veraltet, und seine Implementierung sollte immer `E_NOTIMPL`zurückgeben.  
  
## Syntax  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### Parameter  
 `pbstrSessionName`  
  
## Rückgabewert  
 Diese Methode sollte immer `E_NOTIMPL`zurückgeben.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)