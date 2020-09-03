---
title: 'IDebugExceptionEvent2:: canpasstodebug | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729870"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Bestimmt, ob die Debug-Engine (de) die Option unterstützt, diese Ausnahme an das Programm zu übergeben, das beim Fortsetzen der Ausführung debuggt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Rückgabewert
 Gibt entweder `S_OK` (die Ausnahme kann an das Programm weitergegeben werden) oder `S_FALSE` (die Ausnahme kann nicht weitergegeben werden) zurück.

## <a name="remarks"></a>Bemerkungen
 Die de muss über eine Standardaktion zum übergeben an die zu debuggende Komponente verfügen. Die IDE empfängt möglicherweise das [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) -Ereignis und ruft die [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) -Methode auf, ohne die-Methode aufzurufen `CanPassToDebuggee` . Daher sollte die de über einen Standardfall zum übergeben der Ausnahme verfügen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
