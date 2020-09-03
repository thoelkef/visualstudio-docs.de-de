---
title: 'IDebugCoreServer2:: getportsupplier | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPortSupplier
helpviewer_keywords:
- IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a33fafae142ef0628130d48a9a84d10b408924c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733076"
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Ruft einen bestimmten Port Lieferanten ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortSupplier( 
   REFGUID               guidPortSupplier,
   IDebugPortSupplier2** ppPortSupplier
);
```

```csharp
int GetPortSupplier( 
   ref Guid                guidPortSupplier,
   out IDebugPortSupplier2 ppPortSupplier
);
```

## <a name="parameters"></a>Parameter
`guidPortSupplier`\
in GUID des abzurufenden Port Anbieters.

`ppPortSupplier`\
vorgenommen Gibt ein [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) -Objekt zurück, das den gewünschten Port Lieferanten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
