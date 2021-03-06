---
title: 'IDebugProgramNodeAttach2:: onattach | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721877"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Wird an das zugeordnete Programm angefügt oder den Anfüge Vorgang an die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode.

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
[in] `GUID` , um dem zugeordneten Programm zuzuweisen.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode nicht aufgerufen werden soll. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird während des Anfüge Vorgangs aufgerufen, bevor die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen wird. Die- `OnAttach` Methode kann den Anfüge Vorgang selbst ausführen (in diesem Fall gibt diese Methode zurück `S_FALSE` ) oder den Anfüge Vorgang an die-Methode zurückschieben `IDebugEngine2::Attach` (die- `OnAttach` Methode gibt zurück `S_OK` ). In beiden Ereignissen kann die- `OnAttach` Methode den `GUID` des Programms, das deentschlgt wird, auf den angegebenen festlegen `GUID` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
