---
title: IDebugProgram2::GetProgramId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca86175d34cc1bfd54882adda7e1f7cb464fb22f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212646"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ruft eine GUID für dieses Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parameter
`pguidProgramId`\
[out] Gibt die `GUID` für dieses Programm.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Zurückgeben eine Debug-Engine (DE) die Programm-ID, die ursprünglich übergeben, um die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methoden. Dadurch können die Kennung des Programms über Debugger Komponenten.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)