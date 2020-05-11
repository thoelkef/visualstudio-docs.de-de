---
title: IDebugField::Gleich | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729012"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Diese Methode vergleicht dieses Feld mit dem angegebenen Feld für Gleichheit.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parameter
`pField`\
[in] Das Feld, das mit diesem zu vergleichen ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Felder identisch `S_OK`sind, gibt er zurück. Wenn die Felder unterschiedlich `S_FALSE.` sind, gibt andernfalls einen Fehlercode zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
