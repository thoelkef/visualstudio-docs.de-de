---
title: IDebugStackFrame2::EnumProperties | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5359698b2ae148abd5fc38da346ebcd5c456634c
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

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
 [in] Eine Kombination aus Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind ausgefüllt werden.  
  
 `nRadix`  
 [in] Die Basis bei numerische Formatierungsinformationen verwendet werden soll.  
  
 `refiid`  
 [in] Eine GUID, der einen Filter auswählen, welche verwendet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind, z. B. aufzuzählenden `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung `INFINITE` zum unendlichen Warten angibt.  
  
 `pcelt`  
 [out] Gibt die Anzahl der Eigenschaften aufgelistet. Dies ist der gleiche wie das Aufrufen der [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) Methode.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) Objekt, das eine Liste mit den gewünschten Eigenschaften enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Da diese Methode alle ausgewählte Eigenschaften, die mit einem einzigen Aufruf abgerufen werden kann, ist es schneller als sequenziell Aufrufen der [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) und [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methoden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
