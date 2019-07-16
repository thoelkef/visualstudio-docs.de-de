---
title: IDebugPortNotify2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1b1934a73e096200eba1370320cc0b55eb46ac5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308890"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Diese Schnittstelle registriert oder hebt die Registrierung für ein Programm, das den Port zum Debuggen verwendet werden kann, die es ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen vom Port unterstützt. Sie wird in der Regel implementiert, für das gleiche Objekt, das implementiert die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugPort2` Schnittstelle zurückgibt, diese Schnittstelle. Darüber hinaus einen Aufruf von [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) dieser Schnittstelle zurück. Ein Debugmodul sehen diese Schnittstelle als Parameter an [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugPortNotify2`.

|Methode|Beschreibung|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das Debuggen kann mit dem Port, den es ausgeführt wird.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung für ein Programm, das vom Port debuggt werden kann, die es ausgeführt wird.|

## <a name="remarks"></a>Hinweise
 Es sei denn, ein Debugport erkennen, wenn Programme geladen oder entladen werden, muss ein benutzerdefinierten Port Lieferanten über diese Schnittstelle implementieren. Alle Programme, die geladen werden, für das Debuggen über einen bestimmten Port werden nachverfolgt mithilfe dieser Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)