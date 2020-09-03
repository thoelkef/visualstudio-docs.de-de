---
title: 'IDebugCoreServer3:: GetServerName | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
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
vorgenommen Gibt den Namen des Servers zurück.

> [!NOTE]
> Der Aufrufer ist für das Freigeben der Zeichenfolge verantwortlich.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn Sie einen benutzerfreundlichen Servernamen haben, müssen Sie die [getserverfriendlyname](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
