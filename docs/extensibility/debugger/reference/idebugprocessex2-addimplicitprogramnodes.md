---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9233e2e4b336942e0f67c5b8c52d0928694ae2fd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024863"
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
 [Programmieren von Knoten](../../../extensibility/debugger/program-nodes.md) hinzugefügt werden für jede DE in aufgeführt `rgguidSpecificEngines`– mit Ausnahme der starten-Engine (wie in `guidLaunchingEngine`), dieser wird angenommen, einen eigene Anwendung-Knoten hinzufügen, wenn sie ein Programm gestartet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Programmknoten](../../../extensibility/debugger/program-nodes.md)