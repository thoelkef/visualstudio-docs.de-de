---
title: IDebugProperty2::GetReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49763b0f8a0d7d0c016326d69a22a57d8ff32403
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342934"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Gibt einen Verweis auf den Wert der Eigenschaft zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>Parameter
`ppRererence`\
[out] Gibt eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das einen Verweis auf den Wert der Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurück gegeben, in der Regel `E_NOTIMPL` oder `E_GETREFERENCE_NO_REFERENCE`.

## <a name="see-also"></a>Siehe auch
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)