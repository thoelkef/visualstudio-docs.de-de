---
title: 'Idebugobject:: GetValue | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726541"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ruft den Wert des-Objekts als aufeinander folgende Reihe von Bytes ab.

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
[in, out] Ein Array, das mit einer aufeinanderfolgenden Reihe von Bytes gefüllt ist, die den Wert des-Objekts darstellen.

`nSize`\
in Die maximale Anzahl der abzurufenden bytes.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie die Gesamtzahl der Bytes ab, die durch Aufrufen der [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) -Methode abgerufen werden können.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
