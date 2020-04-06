---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736240"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ruft einen Enumerator aller Elemente des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt ein [IEnumDebugObjects-Objekt](../../../extensibility/debugger/reference/ienumdebugobjects.md) zurück, mit dem alle Elemente aufgezählt werden können.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Alternativ verwenden Sie die [GetCount-](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) und [GetElement-Methoden,](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) um die Elemente zu durchlaufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
