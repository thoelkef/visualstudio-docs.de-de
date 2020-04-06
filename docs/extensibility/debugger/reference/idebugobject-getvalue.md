---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726541"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ruft den Wert des Objekts als eine fortlaufende Reihe von Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parameter
`pValue`\
[in, out] Ein Array, das mit einer aufeinanderfolgenden Reihe von Bytes gefüllt wird, die den Wert des Objekts darstellen.

`nSize`\
[in] Die maximale Anzahl von Bytes, die abgerufen werden sollen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie die Gesamtzahl der Wertbytes ab, die durch Aufrufen der [GetSize-Methode](../../../extensibility/debugger/reference/idebugobject-getsize.md) abgerufen werden können.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
