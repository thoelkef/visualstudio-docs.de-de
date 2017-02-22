---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
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
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der für Codepfade einer angegebenen Position in einer Quelldatei ab.  
  
## Syntax  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### Parameter  
 `pszHint`  
 \[in\]  Das Wort unter dem Cursor in der **Quelle** oder **Disassembly** Ansicht in der IDE.  
  
 `pStart`  
 \[in\]  Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das den aktuellen Kontext Code darstellt.  
  
 `pFrame`  
 \[in\]  Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\-Objekt, das den Stapelrahmen zugeordneten dem aktuellen Haltepunkt darstellt.  
  
 `fSource`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), wenn in der **Quelle** Sicht oder`FALSE`\(null\), wenn in der **Disassembly** Ansicht.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)\-Objekt zurück, das eine Liste von Codepfaden enthält.  
  
 `ppSafety`  
 \[out\]  Gibt ein Objekt zurück, das einen [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) als Haltepunkt darstellt, zusätzlichen Code Elementkontext festgelegt werden, wenn der ausgewählte Codepfad übersprungen wird.  Dies kann im Falle eines kurzgeschlossenen booleschen Ausdrucks ausgeführt, z.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Codepfad beschreibt den Namen einer Methode oder eine Funktion, die aufgerufen wurde, um zum aktuellen Zeitpunkt für die Ausführung des Programms abzurufen.  Eine Liste von Codepfaden stellt die Aufrufliste dar.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)