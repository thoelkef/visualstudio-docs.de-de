---
title: IDebugMethodField::EnumLocals | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a99fb1e0b8b32f98d06f34ac39b8dfd781cdc62
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211977"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Erstellt einen Enumerator für die ausgewählten lokalen Variablen der Methode.

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
[in] Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt, das die debugadresse, die den Kontext oder Gültigkeitsbereich aus der die lokalen Variablen abgerufen wählt darstellt.

`ppLocals`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das eine Liste mit den lokalen darstellt; andernfalls gibt Sie einen null-Wert zurück, wenn kein lokal vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn kein lokal vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Nur die Variablen, die innerhalb des Blocks mit der angegebenen Adresse definiert werden aufgelistet. Wenn alle "lokal", einschließlich alle vom Compiler generierter "lokal" erforderlich sind, rufen Sie die [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) Methode.

Eine Methode kann mehrere Bereichsdefinition Kontexte oder Blöcke enthalten. Beispielsweise enthält die folgende, aus der Luft gegriffen Methode drei Bereiche, die zwei inneren Blöcke und des Methodentexts selbst.

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

Die [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt stellt die `func` Methode selbst. Aufrufen der `EnumLocals` -Methode mit einer [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) legen Sie auf der `Inner Scope 1` Adresse zurückgibt, eine Enumeration mit den `temp1` Variablen, z. B.

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
