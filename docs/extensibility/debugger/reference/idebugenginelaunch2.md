---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730494"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Wird von einem Debugmodul (DE) zum Starten und Beenden von Programmen verwendet.

## <a name="syntax"></a>Syntax

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer benutzerdefinierten DE implementiert, wenn sie spezielle Anforderungen zum Starten eines Prozesses hat, der nicht vollständig von einem benutzerdefinierten Port verarbeitet werden kann. Dies ist in der Regel der Fall, wenn die DE Teil eines Interpreters ist und der zu debuggende Prozess ein Skript ist: Der Interpreter muss zuerst gestartet werden, und dann wird das Skript geladen und gestartet. Ein Port kann den Interpreter starten, aber das Skript kann eine spezielle Handhabung erfordern (wobei die DE eine Rolle spielt). Diese Schnittstelle wird nur implementiert, wenn eindeutige Anforderungen zum Starten eines Programms bestehen, die von einem benutzerdefinierten Port nicht verarbeitet werden können.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird vom Session Debug Manager (SDM) aufgerufen, wenn das SDM diese Schnittstelle von der [IDebugEngine2-Schnittstelle](../../../extensibility/debugger/reference/idebugengine2.md) (mit QueryInterface) abrufen kann. Wenn diese Schnittstelle erhalten werden kann, weiß das SDM, dass die DE spezielle Anforderungen hat und ruft diese Schnittstelle auf, um das Programm zu starten, anstatt es vom Port starten zu lassen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEngineLaunch2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Startet einen Prozess mit der DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Setzt die Prozessausführung fort.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Beendet einen Prozess.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
