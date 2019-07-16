---
title: IDebugMethodField::EnumArguments | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0c5f95267948b6fb2c1cab1a7d79a2e62b9e3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346784"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Erstellt einen Enumerator für den Typ jedes Arguments erforderlich, um die Methode aufrufen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Argumenttypen darstellt. Gibt einen null-Wert zurück, wenn keine Argumente vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine Argumente vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das die Typen der einzelnen Parameter darstellt. Rufen Sie die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode zum Abrufen von Informationen über den Typ jedes Parameters.

 Wenn der Name des Parameters zusammen mit dem Typ erforderlich ist, rufen Sie die [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)