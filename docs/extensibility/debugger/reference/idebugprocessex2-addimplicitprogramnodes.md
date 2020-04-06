---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723398"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Diese Methode fügt einen Programmknoten für jedes angegebene Debugmodul (DE) hinzu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parameter
`guidLaunchingEngine`\
[in] Die `GUID` einer DE, die zum Starten von Programmen verwendet werden soll (und von der angenommen wird, dass sie eigene Programmknoten hinzufügt).

`rgguidSpecificEngines`\
[in] Array `GUID`von dEs von DEs, für die Programmknoten hinzugefügt werden.

`celtSpecificEngines`\
[in] Die Anzahl `GUID`der `rgguidSpecificEngines` s im Array.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [Programmknoten](../../../extensibility/debugger/program-nodes.md) werden für jede DE `rgguidSpecificEngines`hinzugefügt, die in —mit `guidLaunchingEngine`Ausnahme des Startmoduls (wie in angegeben ) aufgeführt ist, von dem angenommen wird, dass er beim Starten eines Programms einen eigenen Programmknoten hinzufügt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Programmknoten](../../../extensibility/debugger/program-nodes.md)
