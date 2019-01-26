---
title: IDebugReference2::GetReferenceInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04a66aed4f086bc8521195cbb8711f181cfcbfe0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952625"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur, die einen Verweis beschreibt. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, die bestimmen, die Felder in ausgefüllt werden, müssen die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur.  
  
 `nRadix`  
 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung `INFINITE` für Warten ohne Timeout.  
  
 `rgpArgs`  
 [in] Ein Array von [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekte. Für die zukünftige Verwendung reserviert. Legen Sie auf einen null-Wert.  
  
 `dwArgCount`  
 [in] Die Anzahl der Verweisargumente in der `rgpArgs` Array. Für die zukünftige Verwendung reserviert. auf 0 festgelegt.  
  
 `pReferenceInfo`  
 [out] Ein [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur, die mit einer Beschreibung der Eigenschaft gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)