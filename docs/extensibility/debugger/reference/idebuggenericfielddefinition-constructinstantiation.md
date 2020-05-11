---
title: IDebugGenericFieldDefinition::KonstruktInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352018e50b955ed414af974bc21b62775fd55f53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728261"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Erstellt eine Feldinstanz, die ein Array von Typargumenten erhält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parameter
`cArgs`\
[in] Anzahl der Argumente `ppArgs` im Array.

`ppArgs`\
[in] Array, das die Typargumente enthält. Die Typargumente müssen geschlossene Typen sein (nicht generische oder vollständig instanziierte Generika).

`ppConstructedField`\
[out] Gibt die [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) zurück, die das neue Feld darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Einschränkungen werden nicht überprüft.

## <a name="see-also"></a>Weitere Informationen
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
