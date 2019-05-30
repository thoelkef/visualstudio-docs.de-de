---
title: IDebugProgramHost2::GetHostName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 851905a9ca642f029444a2f6c1adfdfe543fdf70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351271"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ruft ab, der Titel, Anzeigename oder der Dateiname des Hostprozesses dieses Programms.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parameter
`dwType`\
[in] Ein Wert aus der [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Enumeration.

`pbstrHostName`\
[out] Gibt den angeforderten Namen des Hostprozesses.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In einer typischen Implementierung dieser Methode die `dwType` Parameter wird ignoriert, und ein Benutzerfreundlicher Namen des Hostcomputers wird zurückgegeben. Eine andere mögliche Implementierung besteht darin, übergeben die `dwType` Parameter, um einen Aufruf der [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) Methode, um den Namen zu erhalten.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)