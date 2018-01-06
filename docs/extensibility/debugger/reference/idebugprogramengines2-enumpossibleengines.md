---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 81765959c0735080141ba8974387d592a461df25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Gibt die GUIDs für alle der möglichen Debugmodule (DE), die dieses Programm debuggen können.  
  
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
 [in] Die Anzahl der DE GUIDs zurückgeben. Hiermit wird die maximale Größe der auch die `rgguidEngines` Array.  
  
 `rgguidEngines`  
 [in, out] Ein Array von DE-GUIDs in gefüllt werden soll.  
  
 `pceltEngines`  
 [out] Gibt die tatsächliche Anzahl von DE-GUIDs, die zurückgegeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. [C++] gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` oder [c#] 0x8007007A, wenn der Puffer nicht groß genug ist.  
  
## <a name="remarks"></a>Hinweise  
 Um zu bestimmen, wie viele Module vorhanden sind, rufen Sie diese Methode einmal mit der `celtBuffer` Parameter auf 0 festgelegt und der `rgguidEngines` -Parameter auf einen null-Wert festgelegt. Dies gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A für c#), und die `pceltEngines` Parameter gibt die erforderliche Größe des Puffers zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)