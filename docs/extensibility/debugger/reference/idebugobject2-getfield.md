---
title: 'IDebugObject2:: GetField | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0cd44b655669adec6722bf85223f786210d37de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726220"
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
Ruft den Typ dieses-Objekts ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetField(
 IDebugField** ppField
);
```

```csharp
int GetField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt zurück, wenn kein NULL-Wert ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Feld beschreibt den Typ des Objekts.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
