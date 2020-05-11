---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720933"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Sitzungsdebug-Manager (SDM) gesendet, wenn eine Eigenschaft erstellt wird, die einem bestimmten Dokument zugeordnet ist.

## <a name="syntax"></a>Syntax

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft erstellt wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen. Diese Schnittstelle wird implementiert, wenn die DE eine Eigenschaft erstellt hat, die einem Skript zugeordnet ist, das geladen oder erstellt wurde, und wenn dieses Skript in der IDE angezeigt werden muss.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um zu melden, dass eine Eigenschaft erstellt wurde. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPropertyCreateEvent2` die Methode der Schnittstelle.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ruft die neue Eigenschaft ab.|

## <a name="remarks"></a>Bemerkungen
 Wenn einer Eigenschaft ein bestimmtes Dokument oder Skript zugeordnet ist, kann die DE dieses Ereignis an das SDM senden, um das Fenster **Skriptdokumente** mit dem Namen des Dokuments zu aktualisieren. Das SDM ruft [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) `guidDocument` mit dem `VARIANT` Argument auf, einen mit einem [IUnknown-Zeiger](/cpp/atl/iunknown) abzurufen. Das SDM ruft [QueryInterface](/cpp/atl/queryinterface) unter diesem Zeiger auf, um die [IDebugDocument2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocument2.md) abzurufen, die zum Aktualisieren des **Fensters Skriptdokumente** verwendet wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
