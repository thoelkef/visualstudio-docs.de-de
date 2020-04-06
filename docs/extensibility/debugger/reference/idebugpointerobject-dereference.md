---
title: IDebugPointerObject::Deverweis | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
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
[in] Ein einfacher Byteversatz vom Anfang des Objekts, auf das verwiesen wird.

`ppObject`\
[out] Gibt ein [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das Objekt darstellt, auf das verwiesen wird, plus ggf. Offset.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht auf ein anderes Objekt aufführt.

## <a name="remarks"></a>Bemerkungen
 Das Objekt, auf das verwiesen wird, kann ein primitiver oder komplexerer Typ sein, z. B. eine Klasse oder Struktur.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
