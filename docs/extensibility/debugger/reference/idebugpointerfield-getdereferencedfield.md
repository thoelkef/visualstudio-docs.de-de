---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725623"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Diese Methode gibt den Objekttyp zurück, auf den dieses Zeigerobjekt verweist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
[out] Gibt ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Typ des Zielobjekts beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn z. B. das [IDebugPointerField-Objekt](../../../extensibility/debugger/reference/idebugpointerfield.md) auf eine ganze Zahl verweist, beschreibt der von dieser Methode [zurückgegebene IDebugField-Typ](../../../extensibility/debugger/reference/idebugfield.md) diesen Ganzzahltyp.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
