---
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00954ceaa0ddd750a3d08e372d1edaa1905f01c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724738"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Fügt einen Port hinzu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parameter
`pRequest`\
[in] Ein [IDebugPortRequest2-Objekt,](../../../extensibility/debugger/reference/idebugportrequest2.md) das den hinzuzufügenden Port beschreibt.

`ppPort`\
[out] Gibt ein [IDebugPort2-Objekt](../../../extensibility/debugger/reference/idebugport2.md) zurück, das den Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erstellt tatsächlich den angeforderten Port und fügt ihn der internen Liste der aktiven Ports des Portlieferanten hinzu. Die [CanAddPort-Methode](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) kann zuerst aufgerufen werden, um mögliche zeitaufwändige Verzögerungen zu vermeiden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
