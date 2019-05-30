---
title: IDebugAlias2::GetAppDomainId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40d52c5eedf0defb845f1944acd166d48dca1ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338172"
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