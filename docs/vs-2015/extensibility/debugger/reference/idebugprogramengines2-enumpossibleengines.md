---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946464"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt zurück, die GUIDs für alle der möglichen Debug-Engines (DE), die das Programm debuggen können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
