---
title: IDebugContainerField::EnumFields | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6d3edeb677af728b1a0fd0e9cf8685e7919d79e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317933"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Erstellt einen Enumerator für die Felder des Containers.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwKindFilter`\
[in] Eine Kombination von [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Konstanten, die die Felder aufgelistet werden sollen. Feld-Arten können Speichertypen, z. B. Klasse oder primitive-Typs oder bestimmte Informationen, z. B. lokale, Parameter oder "this"-Zeigers zu beschreiben.

`dwModifiersFilter`\
[in] Eine Kombination von [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Konstanten, die die Felder aufgelistet werden sollen. Feldmodifizierern können Zugriffsberechtigungen, wie z. B. öffentliche oder Private oder Storage-Informationen, z. B. virtuelle, statisch oder abschließend sein.

`pszNameFilter`\
[in] Der Name des Felds, das aufgelistet werden. Dies kann ein null-Wert sein, wenn alle Felder sind, zurückgegeben werden.

`nameMatch`\
[in] Ein Wert aus der [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) -Enumeration, der steuert, ob die Suche nach Groß-/Kleinschreibung beachtet wird, oder nicht.

`ppEnum`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Felder darstellt. Gibt einen null-Wert zurück, wenn keine Felder vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder S_FALSE zurück, wenn keine Felder vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die `dwKindFilter`, `dwModifiersFilter`, und `pszNameFilter` Parameter können kombiniert werden, z. B. alle öffentliche virtuelle Methoden, die mit dem Namen "MyMethod" auswählen.

## <a name="see-also"></a>Siehe auch
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)