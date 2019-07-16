---
title: IDebugPointerObject::Dereference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 381c6f392cccb398497204cc5772c5f9a00fd5b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331662"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ruft das Objekt, das auf den verwiesen wird.

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
[in] Ein einfaches Byteoffset vom Beginn des Objekts verweist.

`ppObject`\
[out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das Objekt darstellt, auf den verwiesen wird, sowie Werte für offset, sofern vorhanden.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht in ein anderes Objekt verweist.

## <a name="remarks"></a>Hinweise
 Das Objekt, das auf den verwiesen wird, kann ein primitiver Typ oder ein komplexer Typ wie z. B. eine Klasse oder Struktur sein.

## <a name="see-also"></a>Siehe auch
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)