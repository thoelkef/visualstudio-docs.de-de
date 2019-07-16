---
title: IDebugPointerObject::GetBytes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 247e1ff4c934ae581c7a0224c8f8cba8d4e9d946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308867"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ruft den Wert als eine Reihe von aufeinander folgenden Bytes gezeigt wird.

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
[in] Ein Offset in Bytes vom Beginn des Objekts auf den verwiesen wird.

`dwCount`\
[in] Die Anzahl der abzurufenden Bytes.

`pBytes`\
[in, out] Ein Array, das mit dem Wert als eine Reihe von aufeinander folgenden Bytes gefüllt ist, auf die am angegebenen Offset aus dem Objekt ab.

`pdwBytes`\
[out] Gibt die Anzahl der Bytes, die tatsächlich abgerufen.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, wenn der Zeiger, dargestellt durch diese [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) verweist auf einen primitiven Typ oder einem einfachen Array primitiver Typen (d. h. ein Array, das durch eine einfache Folge von Bytes dargestellt werden können).

## <a name="see-also"></a>Siehe auch
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)