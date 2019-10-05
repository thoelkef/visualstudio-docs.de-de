---
title: IDebugProgram2::EnumCodePaths | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202769"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste der Codepfade für eine bestimmte Position in einer Quelldatei.  
  
## <a name="syntax"></a>Syntax  
  
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
 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das der aktuelle Codekontext darstellt.  
  
 `pFrame`  
 [in] Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Objekt dem aktuellen Haltepunkt zugeordnet, das den Stapelrahmen darstellt.  
  
 `fSource`  
 [in] Ungleich Null (`TRUE`) sofern es sich um die **Quelle** Ansicht oder 0 (null) (`FALSE`) sofern es sich um die **Disassembly** anzeigen.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) -Objekt, das eine Liste der Codepfade enthält.  
  
 `ppSafety`  
 [out] Gibt eine [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das einen zusätzlicher Codekontext als Haltepunkt festgelegt werden, für den Fall, dass der ausgewählte Pfad code darstellt, wird übersprungen. Dies kann z. B. im Fall von einem kurzgeschlossen booleschen Ausdruck vorkommen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Codepfad beschreibt den Namen einer Methode oder Funktion, um auf die aktuelle bei der Ausführung des Programms erhalten aufgerufen wurde. Eine Liste von Codepfaden stellt dar, die Aufrufliste.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
