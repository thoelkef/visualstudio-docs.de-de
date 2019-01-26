---
title: IDebugStackFrame2::EnumProperties | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a997db37aa980afe1d4eb3bd2728017b6276e23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999365"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Erstellt einen Enumerator für den Stapelrahmen, z. B. lokale Variablen zugeordneten Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 [in] Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind gefüllt werden soll.  
  
 `nRadix`  
 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `refiid`  
 [in] Eine GUID eines Filters zum auswählen, welche [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind, z. B. aufzuzählenden `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung `INFINITE` für Warten ohne Timeout.  
  
 `pcelt`  
 [out] Gibt die Anzahl der aufgelisteten Eigenschaften zurück. Dies ist der gleiche wie das Aufrufen der [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) Methode.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt, das eine Liste der gewünschten Eigenschaften enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Da diese Methode alle ausgewählte Eigenschaften, die mit einem einzigen Aufruf abgerufen werden kann, ist es schneller als sequenziell Aufrufen der [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) und [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methoden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)