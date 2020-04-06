---
title: IEnumDebugReferenceInfo2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Reset
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Reset
ms.assetid: cf8ce649-5ce1-44a6-9d5a-89760021bde4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06d22f9b183352314c7554da9481290328a3865e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715303"
---
# <a name="ienumdebugreferenceinfo2reset"></a>IEnumDebugReferenceInfo2::Reset
Setzt die Enumeration auf das erste Element zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Next-Methode](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md) das erste Element der Enumeration zurück.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
