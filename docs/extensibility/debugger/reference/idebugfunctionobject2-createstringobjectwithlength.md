---
title: IDebugfunctionObject2::CreateStringObjectWithLength | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 937d325f8637a3260121def189d472dcfb3e1309
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728467"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Erstellt ein Zeichenfolgenobjekt mit der angegebenen Länge.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pcstrString`\
[in] Der Zeichenfolgenwert für das Zeichenfolgenobjekt.

`uiLength`\
[in] Die Länge der Zeichenfolge in Bytes.

`ppObject`\
[out] Gibt ein [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Zeichenfolgenobjekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
