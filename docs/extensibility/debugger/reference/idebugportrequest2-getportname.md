---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724816"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ruft den Namen des Ports ab.

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
[out] Gibt den Namen des Ports zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [IDebugPortRequest2-Schnittstelle](../../../extensibility/debugger/reference/idebugportrequest2.md) wird normalerweise von einem Debugpaket (dem Client) an einen Portlieferanten (den Server) übergeben, um eine Verbindung zu einem Port zu erhalten. Sowohl das Debugpaket als auch der Portlieferant sind sich der möglichen Optionen für den Port bewusst. Wenn eine einfache Zeichenfolge den Port `IDebugPortRequest2::GetPortName` beschreiben kann, verfügt die Methode über genügend Informationen, um die Verbindung herzustellen. Andernfalls können zusätzliche Schnittstellen vom Client bereitgestellt werden, die vom `IDebugPortRequest2::QueryInterface`Server mithilfe von abgerufen werden können.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
