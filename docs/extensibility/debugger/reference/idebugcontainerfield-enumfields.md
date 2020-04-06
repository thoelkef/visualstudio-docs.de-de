---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733225"
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
[in] Eine Kombination [aus FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Konstanten, die die Felder auswählen, die aufgezählt werden sollen. Feldtypen können Speichertypen wie Klasse oder Primitiv oder bestimmte Informationen wie lokale, Parameter oder "this"-Zeiger beschreiben.

`dwModifiersFilter`\
[in] Eine Kombination aus [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Konstanten, die die Felder auswählen, die aufgezählt werden sollen. Feldmodifikatoren können Zugriffsberechtigungen sein, z. B. öffentliche oder private, oder Speicherinformationen, z. B. virtuelle, statische oder endgültige.

`pszNameFilter`\
[in] Der Name des Felds, das aufgezählt werden soll. Dies kann ein NULL-Wert sein, wenn alle Felder zurückgegeben werden sollen.

`nameMatch`\
[in] Ein Wert [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) aus der NAME_MATCH-Enumeration, die steuert, ob bei der Suche die Groß-/Kleinschreibung beachtet wird oder nicht.

`ppEnum`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der Felder darstellt. Gibt einen NULL-Wert zurück, wenn keine Felder vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Felder vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die `dwKindFilter` `dwModifiersFilter`, `pszNameFilter` und Parameter können kombiniert werden, um z. B. alle öffentlichen virtuellen Methoden mit dem Namen "MyMethod" auszuwählen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
