---
title: IDebugPointerObject::GetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725519"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ruft den Wert ab, auf den als eine Reihe aufeinander folgender Bytes verwiesen wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parameter
`dwStart`\
[in] Ein Offset in Bytes vom Anfang des Objekts, auf das verwiesen wird.

`dwCount`\
[in] Die Anzahl der abzurufenden Bytes.

`pBytes`\
[in, out] Ein Array, das mit dem Wert als eine Reihe aufeinander folgender Bytes ausgefüllt wird, beginnend mit dem angegebenen Offset vom Objekt, auf das verwiesen wird.

`pdwBytes`\
[out] Gibt die Anzahl der tatsächlich abgerufenen Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn der Zeiger, wie er durch dieses [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt wird, auf einen primitiven Typ oder ein einfaches Array primitiver Typen (d. h. ein Array, das durch eine einfache Sequenz von Bytes dargestellt werden kann) verweist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [Setbytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
