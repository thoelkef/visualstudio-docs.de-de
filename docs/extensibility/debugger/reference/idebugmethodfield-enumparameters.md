---
title: IDebugMethodField::EnumParameters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f9894d7076ef992854a2acc2ac7a7a519b26109
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723642"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Erstellt einen Enumerator für die Parameter der Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

#### <a name="parameters"></a>Parameter
 `ppParams`

 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Parameter der Methode darstellt, andernfalls einen null-Wert, wenn keine Parameter vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine Parameter vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das verschiedene Arten von Parametern darstellt. Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Methode für jedes Objekt, um zu bestimmen, genau die Art der Parameter das Objekt darstellt.

 Ein Parameter enthält den Namen der Variable und ihren Typ gleichzeitig. Der erste Parameter an eine Klassenmethode wird in der Regel das "this"-Zeigers.

 Wenn nur die Typen der Parameter erforderlich ist, rufen die [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)