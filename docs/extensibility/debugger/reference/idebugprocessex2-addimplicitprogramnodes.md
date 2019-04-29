---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6203b12defbe70d3807508953d85f39ff725a746
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917603"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Diese Methode fügt einen Programm-Knoten für jede Debug-Engine (DE) angegeben.

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

#### <a name="parameters"></a>Parameter
 `guidLaunchingEngine`

 [in] Die `GUID` von einer bereitgestellten Kompatibilitätsrichtlinie, die verwendet werden soll, um Programme zu starten (und wird davon ausgegangen, dass eine eigene Anwendung Knoten hinzufügen).

 `rgguidSpecificEngines`

 [in] Array von `GUID`s DEs, welches Programm Knoten hinzugefügt werden.

 `celtSpecificEngines`

 [in] Die Anzahl der `GUID`s in der `rgguidSpecificEngines` Array.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
- [Programmieren von Knoten](../../../extensibility/debugger/program-nodes.md) hinzugefügt werden für jede DE in aufgeführt `rgguidSpecificEngines`– mit Ausnahme der starten-Engine (wie in `guidLaunchingEngine`), dieser wird angenommen, einen eigene Anwendung-Knoten hinzufügen, wenn sie ein Programm gestartet wird.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Programmknoten](../../../extensibility/debugger/program-nodes.md)