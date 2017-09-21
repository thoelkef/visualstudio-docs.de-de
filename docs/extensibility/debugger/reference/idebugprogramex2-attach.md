---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügen Sie eine Sitzung mit einem Programm an.  
  
## Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### Parameter  
 `pCallback`  
 \[in\]  Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt, das die Rückruffunktion zeigt, dass das Debugmodul für angefügte Ereignisse sendet.  
  
 `dwReason`  
 \[in\]  Ein Wert aus der [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)\-Enumeration, der den Grund für den Anfügevorgang zu beschreiben.  
  
 `pSession`  
 \[in\]  Ein Wert, der die Sitzung eindeutig identifiziert wird, die dem Programm angefügt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Diese Methode sollte `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` zurückgeben, wenn das Programm bereits angefügt ist.  
  
## Hinweise  
 Der Anschluss, der das Programm enthält, kann der Wert in `pSession` verwenden, um zu bestimmen, welche Sitzung versucht, auf das Programm anzufügen.  Wenn beispielsweise ein Port nur eine Debugsitzung zur Anfügen an einen Prozess auf einmal zulässt, kann der Anschluss bestimmen, ob die gleiche Sitzung bereits in anderen Programmen im Prozess angefügt wird.  
  
> [!NOTE]
>  Die Schnittstelle, die in `pSession` übergeben wird, soll nur als Cookie behandelt werden, ein Wert, der den Debug\- Manager der Sitzung eindeutig identifiziert, der an diesem Programm angefügt wird. Keine Methoden für die angegebene Schnittstelle sind aktiviert.  
  
## Siehe auch  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)