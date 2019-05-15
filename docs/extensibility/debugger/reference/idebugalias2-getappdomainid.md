---
title: IDebugAlias2::GetAppDomainId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17f6e487dee1b5ae490cfc2ab180eb872ed5b5d2
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615094"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Ruft den Bezeichner für die Anwendungsdomäne ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parameter
`pappDomainId`\
[out] Gibt den Bezeichner der Anwendungsdomäne zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Anwendung Domäne Bezeichner ändern, wenn die Anwendung neu gestartet wird und eine neue Anwendungsdomäne erstellt wird.

## <a name="see-also"></a>Siehe auch
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)