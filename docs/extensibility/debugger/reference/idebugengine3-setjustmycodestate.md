---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt das Debugmodul zu den JustMyCode\-Zustandsinformationen.  
  
## Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### Parameter  
 `fUpdate`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), um den aktuellen Informationen zu aktualisieren,`FALSE`\(null\), um alle Daten zurückzusetzen und Kleinschreibung erfolgen soll \(der gesamte Inhalt bereits festgelegt\).  
  
 `dwModules`  
 \[in\]  Anzahl von Informationen in `rgJMCSpec.`strukturen  
  
 `rgJMCSpec`  
 \[in\]  Array von Strukturen [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) zu verwenden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 JustMyCode ist das Konzept des Debuggens nur von Code, der einem Benutzer und dem Ignorieren zwischen allen Code wie System gehört, das Code\-gleichmäßig ist, wenn Quellcode für den Systemcode verfügbar ist.  
  
## Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)