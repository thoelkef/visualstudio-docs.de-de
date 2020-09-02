---
title: 'Idebugarrayobject:: getElements | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736240"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ruft einen Enumerator für alle Elemente des Arrays ab.

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
vorgenommen Gibt ein [ienumdebugobjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) -Objekt zurück, das das Auflisten aller Elemente ermöglicht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie als Alternative die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) -Methode und die [getelate](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) -Methode, um die Elemente zu durchlaufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
