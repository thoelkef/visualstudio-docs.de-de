---
title: IDebugCoreServer3::GetServerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf8233a4e2e37478a5818da2c27e498fcf954de9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732865"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
Ruft den Namen des Servers ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
[out] Gibt den Namen des Servers zurück.

> [!NOTE]
> Der Aufrufer ist für die Freigabe der Zeichenfolge verantwortlich.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie für einen freundlichen Servernamen die [GetServerFriendlyName-Methode](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
