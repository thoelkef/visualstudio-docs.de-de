---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
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
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob das Debugmodul \(DE\) die Übergabe dieser Ausnahme in das Programm, das gedebuggt wird unterstützt, wenn die Ausführung fortgesetzt wird.  
  
## Syntax  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## Rückgabewert  
 Gibt entweder `S_OK` \(die Ausnahme kann an das Programm übergeben werden\) oder `S_FALSE` zurück \(die Ausnahme kann keine Verbindung übergeben werden.\)  
  
## Hinweise  
 DE muss eine Standardaktion für die Übergabe zu debuggende Komponente verfügen.  Die IDE das [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)\-Ereignis empfangen und ruft die [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)\-Methode aufrufen, ohne die `CanPassToDebuggee`\-Methode aufzurufen.  Deshalb sollte DE einem Standardargument oder für die Ausnahme an.  
  
## Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)