---
title: 'IDebugEngine2:: removeallabtexceptions | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5ac703f1d0bd374131a4f5de397f39cf0ba209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731030"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Entfernt die Liste der Ausnahmen, die die IDE für eine bestimmte Lauf Zeit Architektur oder-Sprache festgelegt hat.

## <a name="syntax"></a>Syntax

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parameter
`guidType`\
in Entweder die GUID für die Sprache oder die GUID für die Debug-Engine, die für eine Lauf Zeit architekturspezifisch ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Ausnahmen, die von dieser Methode entfernt wurden, wurden von früheren Aufrufen der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) -Methode festgelegt.

 Um eine bestimmte Ausnahme zu entfernen, müssen Sie die [removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
