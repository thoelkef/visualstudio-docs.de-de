---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3ebf30c4152e03a72626b96cfd51b0341494ccb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891384"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Gibt zurück, die GUIDs für alle der möglichen Debug-Engines (DE), die das Programm debuggen können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celtBuffer`  
 [in] Die Anzahl der DE-GUIDs, die zurückgegeben werden soll. Hiermit wird die maximale Größe der auch die `rgguidEngines` Array.  
  
 `rgguidEngines`  
 [in, out] Ein Array von DE-GUIDs gefüllt werden soll.  
  
 `pceltEngines`  
 [out] Gibt die tatsächliche Anzahl von DE-GUIDs, die zurückgegeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` oder [C#] 0x8007007A, wenn der Puffer nicht groß genug ist.  
  
## <a name="remarks"></a>Hinweise  
 Um zu bestimmen, wie viele Module vorhanden sind, rufen diese Methode einmal mit der `celtBuffer` -Parameter auf 0 festgelegt und die `rgguidEngines` -Parameter auf einen null-Wert festgelegt. Dies gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A für C#-Code), und die `pceltEngines` Parameter gibt die erforderliche Größe des Puffers zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)