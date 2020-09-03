---
title: Idebugpointerobject::D ereferenzierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725576"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ruft das Objekt ab, auf das verwiesen wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`dwIndex`\
in Ein einfacher Byte Offset vom Anfang des Objekts, auf das verwiesen wird.

`ppObject`\
vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das Objekt darstellt, auf das verwiesen wird, plus Offset, falls vorhanden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht auf ein anderes Objekt verweist.

## <a name="remarks"></a>Bemerkungen
 Das Objekt, auf das gezeigt wird, kann ein primitiver oder komplexer Typ sein, z. b. eine Klasse oder Struktur.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
