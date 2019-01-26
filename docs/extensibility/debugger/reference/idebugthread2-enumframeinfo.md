---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b329dd0c7a1ef7451a40d36ecbb10690e7b70ca3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956531"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Ruft eine Liste der Stapelrahmen für diesen Thread.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 [in] Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, der angibt, welche Felder von der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen sind ausgefüllt werden müssen. Geben Sie die `FIF_FUNCNAME_FORMAT` Flag, um den Namen der Funktion in einer einzelnen Zeichenfolge formatieren.  
  
 `nRadix`  
 [in] Die Basis, die in die numerische Formatierungsinformationen im Enumerator verwendet.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Objekt, das eine Liste der enthält [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen, die den Stapelrahmen beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Des Threads Frames werden mit den aktuellen Frame zuerst aufgelistet und der ältesten Rahmen zuletzt aufgelistet in der Reihenfolge aufgelistet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)