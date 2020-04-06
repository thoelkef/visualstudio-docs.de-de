---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725502"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Legt den Wert fest, auf den aus einer Reihe aufeinander folgender Bytes verwiesen wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parameter
`dwStart`\
[in] Ein Offset in Bytes vom Anfang des Objekts, auf das verwiesen wird.

`dwCount`\
[in] Die Anzahl der festzulegenden Bytes.

`pBytes`\
[in] Ein Array von Bytes, die den neuen Wert darstellen. Dieser Wert wird im Objekt gespeichert, beginnend mit dem angegebenen Offset.

`pdwBytes`\
[out] Gibt die Anzahl der tatsächlich festgelegten Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn der Zeiger, wie er durch dieses [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt wird, auf einen primitiven Typ oder ein einfaches Array primitiver Typen (d. h. ein Array, das durch eine einfache Sequenz von Bytes dargestellt werden kann) verweist. Dieses `IDebugPointerObject` Objekt kann kein Nullverweis sein (es muss auf eine Adresse im Speicher verweisen).

## <a name="see-also"></a>Weitere Informationen
- [Getbytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
