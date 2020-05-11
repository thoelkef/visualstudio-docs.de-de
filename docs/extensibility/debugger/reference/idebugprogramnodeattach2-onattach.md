---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721877"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Fügt an das zugeordnete Programm an, oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) verschiebt den Anfügeprozess an die Attach-Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parameter
`guidProgramId`\
[in] `GUID` , um es dem zugeordneten Programm zuzuweisen.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn die [Attach-Methode](../../../extensibility/debugger/reference/idebugengine2-attach.md) nicht aufgerufen werden soll. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird während des Attach-Prozesses aufgerufen, bevor die [Attach-Methode](../../../extensibility/debugger/reference/idebugengine2-attach.md) aufgerufen wird. Die `OnAttach` Methode kann den Attach-Prozess selbst ausführen `S_FALSE`(in diesem Fall gibt `IDebugEngine2::Attach` diese Methode `OnAttach` zurück) oder den Attach-Prozess an die Methode verschieben (die Methode gibt zurück). `S_OK` In beiden Fall `OnAttach` kann die `GUID` Methode die des zu debuggenden Programms auf die angegebene `GUID`festlegen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
