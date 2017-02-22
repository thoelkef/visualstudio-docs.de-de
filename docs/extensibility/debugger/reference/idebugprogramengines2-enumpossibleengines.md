---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
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
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die GUID für alle möglichen Debugmodule zurück \(DE\), die dieses Programm debuggen können.  
  
## Syntax  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### Parameter  
 `celtBuffer`  
 \[in\]  Die Anzahl der DE GUIDs, die zurückgegeben werden soll.  Des Weiteren wird die maximale Größe des `rgguidEngines` Arrays an.  
  
 `rgguidEngines`  
 \[in, out\]  Ein Array von GUIDs DE gefüllt werden soll.  
  
 `pceltEngines`  
 \[out\]  Gibt die tatsächliche Anzahl von GUIDs DE zurück, dessen Größe zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \[C\+\+\] oder \[C\#\] 0x8007007A zurück, wenn der Puffer nicht groß genug ist.  
  
## Hinweise  
 Für die bestimmen, wie viele Module dort diese Methode einmal mit dem `celtBuffer`\-Parameter sind, aufrufen, der auf 0 festgelegt werden, und dem `rgguidEngines`\-Parameter, der auf einen NULL\-Wert festgelegt ist.  Dies gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 0x8007007A \(für C\#\) zurück, und der `pceltEngines`\-Parameter gibt die erforderliche Größe des Puffers zurück.  
  
## Siehe auch  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)