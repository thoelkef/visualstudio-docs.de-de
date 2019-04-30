---
title: IDebugProgramNode2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51f49ca90837cf80c22856ae2e8f89a98da43d86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869962"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Diese Schnittstelle stellt ein Programm, das debuggt werden kann.

## <a name="syntax"></a>Syntax

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul (DE) oder einen benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um ein Programm darstellen, die debuggt werden kann. Diese Schnittstelle wird in der Regel implementiert, für das gleiche Objekt, das implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Diese Schnittstelle ist mit registriert [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) dieser Schnittstelle zurückgegeben. Ein benutzerdefinierten Port Lieferanten empfängt diese Schnittstelle durch einen Aufruf von [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Eine bereitgestellten Kompatibilitätsrichtlinie empfängt diese Schnittstelle durch einen Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramNode2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ruft den Namen eines Programms.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ruft den Namen der Hostprozess für ein Programm ab.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ruft die System-Prozess-ID für den Prozess, der ein Programm hostet.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|ALS VERALTET MARKIERT. VERWENDEN SIE NICHT. Finden Sie unter den [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle für einen alternativen Ansatz.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ruft den Namen und Bezeichner, der die Ausführung dieses Programms DE.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.|

## <a name="remarks"></a>Hinweise
 Ruft die Sitzungs-Debug-Manager (SDM) in der Regel [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) dieser Schnittstelle abgerufen.

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)