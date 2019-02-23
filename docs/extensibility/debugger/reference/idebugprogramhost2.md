---
title: IDebugProgramHost2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadbd74480c990c4e7317244ec225d775347a6c2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692800"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Diese Schnittstelle bietet (Process)-Hostinformationen zu einem Programm.

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine diese Schnittstelle implementiert, auf das gleiche Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um Informationen über den Hostprozess bereitzustellen. Dies ist eine optionale Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProgram2` Schnittstelle, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramHost2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ruft ab, der Titel, Anzeigename oder der Dateiname des Hostprozesses dieses Programms.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ruft die Prozess-ID des Hostprozesses dieses Programms ab.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ruft den Namen des Computers, auf der Hostprozess dieses Programms ausgeführt wird.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)