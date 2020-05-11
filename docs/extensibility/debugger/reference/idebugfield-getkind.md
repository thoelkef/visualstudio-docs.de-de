---
title: IDebugField::GetKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetKind
helpviewer_keywords:
- IDebugField::GetKind method
ms.assetid: e7c9c60a-8e55-4ecc-aa63-0c814a1e92cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 807b4ecab517e151c87bfc5daab3e94a1e7d5f22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728818"
---
# <a name="idebugfieldgetkind"></a>IDebugField::GetKind
Diese Methode erhält die Art des Feldes.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetKind( 
   FIELD_KIND* pdwKind
);
```

```csharp
int GetKind(
   out enum_FIELD_KIND pdwKind
);
```

## <a name="parameters"></a>Parameter
`pdwKind`\
[out] Gibt die Art des Felds als Kombination aus [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) konstanten konstanten.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
