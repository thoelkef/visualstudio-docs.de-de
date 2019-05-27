---
title: IDebugProcess2::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 371766c1aaffbbd82cd4a5da8876a65eccc96363
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202604"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Ruft ab, der Titel, der Anzeigename oder der Dateiname des Prozesses.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

## <a name="parameters"></a>Parameter
`gnType`\
[in] Ein Wert aus der [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Enumeration, der angibt, welche Art von Namen zurückgegeben.

`pbstrName`\
[out] Gibt den Namen des Prozesses.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)