---
title: IDebugPortRequest2::GetPortName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8017237af68b3dc414dc64bf6ae077387f0a600
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340380"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ruft den Namen des Ports.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parameter
`pbstrPortName`\
[out] Gibt den Namen des Ports.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Schnittstelle wird in der Regel aus einem debugpaket (Client) an übergeben eines portanbieters (Server), um eine Verbindung zu erhalten. mit einem Port. Sowohl das debugpaket und Anschlusslieferanten sind die möglichen Optionen für den Port kennen. Wenn Sie eine einfache Zeichenfolge beschrieben, kann den Port, und klicken Sie dann die `IDebugPortRequest2::GetPortName` Methode weist genügend Informationen zum Herstellen die Verbindung. Andernfalls können weitere Schnittstellen bereitgestellt werden, durch den Client, der vom Server mit abgerufen werden kann `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Siehe auch
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)