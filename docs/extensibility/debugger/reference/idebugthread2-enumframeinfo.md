---
title: IDebugThread2::EnumFrameInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98cd9db7785d7d7867e48f0bd56a2f5ab657a344
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942735"
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