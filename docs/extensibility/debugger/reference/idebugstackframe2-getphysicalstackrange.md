---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be53b50bc21d81c60f7131e8ed437ecb2ac2f16c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120841"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ruft eine rechnerabhängige Darstellung des Bereichs von physischen Adressen, die einen Stapelrahmen zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `paddrMin`  
 [out] Gibt die niedrigste physischen Adresse dieses Stapelrahmens zugeordnet.  
  
 `paddrMax`  
 [out] Gibt die höchste physischen Adresse dieses Stapelrahmens zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Informationen, die von dieser Methode zurückgegebene Sitzungs-Debug-Manager (SDM) wird von Stapelrahmen zu sortieren.  
  
 Es wird davon ausgegangen, dass die Aufrufliste nach unten, d. h. vergrößert wird, dass neue Stapelrahmen in zunehmend niedrigeren Speicheradressen hinzugefügt werden. Eine Laufzeit-Architektur muss physischen Stapel Bereiche angeben, die diese Annahme entsprechen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)