---
title: IDebugDefaultPort2 | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732318"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Diese Schnittstelle bietet verschiedene Methoden für den Zugriff auf die Server-und Benachrichtigungsfunktionen eines Ports.

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um den Debugport für den Zugriff auf Programme darzustellen. Ein benutzerdefinierter Port Lieferant kann diese Schnittstelle auch implementieren, wenn er das Remote Debuggen verarbeitet.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird von einem Argument für Methoden in der [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) -Schnittstelle bereitstellt. Das Aufrufen von [QueryInterface](/cpp/atl/queryinterface) für eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle kann diese Schnittstelle ebenfalls abrufen.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)definierten Methoden implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft die Port Benachrichtigungs Schnittstelle von diesem Port ab.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle zum Server ab, der diesen Port gehostet.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Port auf dem lokalen Computer ausgeführt wird.|

## <a name="remarks"></a>Bemerkungen
 Der Name " `IDebugDefaultPort2` " ist ein wenig irreführend, da er keinen Standardport darstellt. Sie kann als "IDebugPort3" bezeichnet werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
