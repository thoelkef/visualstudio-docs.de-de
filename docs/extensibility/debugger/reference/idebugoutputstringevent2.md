---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726018"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Session Debug Manager (SDM) gesendet, um eine Zeichenfolge auszugeben.

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um eine Zeichenfolge an das **Ausgabefenster** der IDE zu senden. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um eine Zeichenfolge an das **Ausgabefenster** zu senden. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugOutputStringEvent2`die Methode von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getstring](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ruft die anzeigebare Meldung ab.|

## <a name="remarks"></a>Bemerkungen
 In nicht verwaltetem Code kann die ausgabeende Zeichenfolge beispielsweise entstehen, wenn das zu debuggende Programm eine Zeichenfolge an die Win32-Funktion `OutputDebugString` sendet. Diese Zeichenfolge wird von der DE abgefangen und `IDebugOutputStringEvent2` als Ereignis an das SDM gesendet.

 Verwenden Sie [IDebugMessageEvent2,](../../../extensibility/debugger/reference/idebugmessageevent2.md) um eine Nachricht zu senden, die eine Benutzerantwort erfordert.

 Verwenden Sie [IDebugErrorEvent2,](../../../extensibility/debugger/reference/idebugerrorevent2.md) um eine Fehlermeldung zu senden, die keine Antwort erfordert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
