---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727205"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Ein [IDebugAddress-Objekt,](../../../extensibility/debugger/reference/idebugaddress.md) das die Debugadresse darstellt, die den Kontext oder Denumfang auswählt, aus dem die Locals abtreten sollen.

`ppLocals`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das eine Liste der Locals darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, wenn keine Locals vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Locals vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Nur die innerhalb des Blocks definierten Variablen, die die angegebene Debugadresse enthalten, werden aufgezählt. Wenn alle Locals einschließlich compilergenerierter Locals benötigt werden, rufen Sie die [EnumAllLocals-Methode](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) auf.

Eine Methode kann mehrere Bereichskontexte oder Blöcke enthalten. Die folgende ausgeklügelte Methode enthält z. B. drei Bereiche, die beiden inneren Blöcke und den Methodenkörper selbst.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

Das [IDebugMethodField-Objekt](../../../extensibility/debugger/reference/idebugmethodfield.md) stellt die `func` Methode selbst dar. Wenn `EnumLocals` Sie die Methode mit einem `Inner Scope 1` [IDebugAddress-Satz](../../../extensibility/debugger/reference/idebugaddress.md) auf `temp1` die Adresse aufrufen, wird z. B. eine Enumeration zurückgegeben, die die Variable enthält.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
