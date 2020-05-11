---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727341"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Erstellt einen Enumerator für alle lokalen Variablen der Methode, einschließlich der von einem Compiler intern generierten Variablen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Ein [IDebugAddress-Objekt,](../../../extensibility/debugger/reference/idebugaddress.md) das eine Debugadresse innerhalb der Methode darstellt und auf einen bestimmten Bereich oder Kontext verweist.

`ppLocals`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste aller Locals im angegebenen Bereich darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, der keine Locals angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Locals vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nur die innerhalb des Blocks definierten Variablen, die die angegebene Debugadresse enthalten, werden aufgezählt. Diese Methode enthält alle vom Compiler generierten Locals. Wenn nur die Inseerstellungen benötigt werden, die explizit in der Quelle definiert sind, rufen Sie die [EnumLocals-Methode](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) auf.

 Eine Methode kann mehrere Bereichskontexte oder Blöcke enthalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
