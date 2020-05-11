---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732318"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Diese Schnittstelle bietet mehrere Methoden für den Zugriff auf den Server und die Benachrichtigungsfunktionen eines Ports.

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um den Debugport für den Zugriff auf Programme darzustellen. Ein benutzerdefinierter Portlieferant kann diese Schnittstelle auch implementieren, wenn er Remote-Debugging verarbeitet.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Argument für Methoden auf der [IDebugProgramProvider2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogramprovider2.md) stellt diese Schnittstelle bereit. Das Aufrufen von [QueryInterface](/cpp/atl/queryinterface) auf einer [IDebugPort2-Schnittstelle](../../../extensibility/debugger/reference/idebugport2.md) kann diese Schnittstelle ebenfalls abrufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)definierten Methoden implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft die Portbenachrichtigungsschnittstelle von diesem Port ab.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle zum Server ab, der diesen Port hostet.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Port auf dem lokalen Computer ausgeführt wird.|

## <a name="remarks"></a>Bemerkungen
 Der Name`IDebugDefaultPort2`" ist ein wenig falsch, da er keinen Standardport darstellt. Es könnte "IDebugPort3" genannt werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
