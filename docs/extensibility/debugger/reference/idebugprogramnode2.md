---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721910"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Diese Schnittstelle stellt ein Programm dar, das gedebuggégiert werden kann.

## <a name="syntax"></a>Syntax

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul (DE) oder ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um ein Programm darzustellen, das gedebuggt werden kann. Diese Schnittstelle wird in der Regel für dasselbe Objekt implementiert, das die [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) implementiert. Diese Schnittstelle wird [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] registriert, indem [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)aufgerufen wird.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) auf, um diese Schnittstelle zurückzugeben. Ein benutzerdefinierter Portlieferant empfängt diese Schnittstelle über einen Aufruf von [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Ein DE empfängt diese Schnittstelle über einen Aufruf an [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgramNode2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ruft den Namen eines Programms ab.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ruft den Namen des Prozesses ab, der ein Programm hostet.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ruft den Systemprozessbezeichner für den Prozess ab, der ein Programm hostet.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Veraltet. NICHT VERWENDEN.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Veraltet. NICHT VERWENDEN. Einen alternativen Ansatz finden Sie in der [IDebugProgramNodeAttach2-Schnittstelle.](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ruft den Namen und den Bezeichner der DE ab, die dieses Programm ausführt.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Veraltet. NICHT VERWENDEN.|

## <a name="remarks"></a>Bemerkungen
 Der Sitzungsdebug-Manager (SDM) ruft in der Regel [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) auf, um diese Schnittstelle abzuerhalten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
