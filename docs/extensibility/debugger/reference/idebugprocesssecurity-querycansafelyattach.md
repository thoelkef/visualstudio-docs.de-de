---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ermöglicht es dem Anschlusslieferanten, um eine Warnung angezeigt, bevor der Benutzer zu einem unsicheren Prozess anfügt.  
  
## Syntax  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## Rückgabewert  
 Die Werte lauten wie folgt:  
  
-   `S_OK`: Die zu verarbeitende das Anfügen ist sicher und keine Warnung Dialog Box wird angezeigt.  
  
-   `S_FALSE`: Das Anfügen kann ein Sicherheitsproblem sein und ein Dialogfeld mit einer Warnung wird angezeigt.  
  
-   `FAILURE`: Die zu verarbeitende das Anfügen schlägt fehl.  
  
## Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)