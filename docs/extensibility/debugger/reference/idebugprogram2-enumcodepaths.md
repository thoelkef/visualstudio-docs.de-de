---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::EnumCodePaths
helpviewer_keywords: IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c9e87e3435f5902e277a2c80c68ab2dab891bd38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Ruft eine Liste der Codepfade einer bestimmten Position in einer Quelldatei ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszHint`  
 [in] Das Wort unter dem Cursor in die **Quelle** oder **Disassembly** Ansicht in der IDE.  
  
 `pStart`  
 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das den aktuellen Codekontext darstellt.  
  
 `pFrame`  
 [in] Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Objekt dem aktuellen Haltepunkt zugeordnet, das den Stapelrahmen darstellt.  
  
 `fSource`  
 [in] Ungleich Null (`TRUE`) sofern in der **Quelle** anzeigen, oder 0 (null) (`FALSE`) sofern in der **Disassembly** anzeigen.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) Objekt, das eine Liste der Codepfade enthält.  
  
 `ppSafety`  
 [out] Gibt eine [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt übersprungen wird, die einen Kontext kein zusätzlicher Code einen Haltepunkt festzulegen, für den Fall, dass der ausgewählte Pfad code darstellt. Dies kann z. B. bei einem kurzgeschlossen booleschen Ausdruck vorkommen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Codepfad beschreibt den Namen einer Methode oder Funktion, die aufgerufen wurde, um auf den aktuellen Punkt in der Ausführung des Programms zu erhalten. Eine Liste der Codepfade darstellt, die Aufrufliste.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)