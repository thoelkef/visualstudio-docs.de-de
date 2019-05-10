---
title: IDebugProperty2::EnumChildren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7158649ee3965127b5bdeba42619eaa676cfaa0
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458921"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Ruft eine Liste der untergeordneten Elemente der Eigenschaft.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
 `dwFields`\

 [in] Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind gefüllt werden soll.

 `dwRadix`\

 [in] Gibt an, die Basis bei der Formatierung von numerischen Informationen verwendet werden.

 `guidFilter`\

 [in] GUID des Filters verwendet wird, mit der `dwAttribFilter` und `pszNameFilter` Parameter auswählen, welche `DEBUG_PROPERTY_INFO` untergeordnet sind, aufgelistet werden sollen. Z. B. `guidFilterLocals` Filter für lokale Variablen.

 `dwAttribFilter`\

 [in] Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, der angibt, welche Objekttypen aufgelistet, z. B. `DBG_ATTRIB_METHOD` für alle Methoden, die untergeordneten Elemente dieser Eigenschaft sein können. In Kombination mit verwendet die `guidFilter` und `pszNameFilter` Parameter.

 `pszNameFilter`\

 [in] Der Name des Filters verwendet wird, mit der `guidFilter` und `dwAttribFilter` Parameter auswählen, welche `DEBUG_PROPERTY_INFO` untergeordnet sind, aufgelistet werden sollen. Dieser Parameter z. B. festlegen "MyX" Filter, für alle untergeordneten Elemente mit dem Namen "MyX."

 `dwTimeout`\

 [in] Gibt die maximale Zeit in Millisekunden, warten Sie vor der Rückgabe dieser Methode an. Verwendung `INFINITE` für Warten ohne Timeout.

 `ppEnum`\

 [out] Gibt eine [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt, das eine Liste der untergeordneten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)