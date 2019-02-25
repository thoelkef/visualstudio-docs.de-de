---
title: IDebugProgram2::EnumModules | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8de1f98cb6953ba713796e1dbd74de849a0aaf7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715935"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Ruft eine Liste der Module, die dieses Programm wurde geladen und ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `ppEnum`

 [out] Gibt eine [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) -Objekt, das eine Liste der Module enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein Modul ist eine DLL oder Assembly und wird in der Regel in der **Module** Debug-Fenster.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)