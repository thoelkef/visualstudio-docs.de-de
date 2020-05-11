---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736618"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Das Debugmodul (DE) verwendet diese Schnittstelle, um ein dokument zu laden.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, wenn eine Quelldatei geöffnet werden muss. Diese Schnittstelle wird nur von Debugmodulen implementiert, die mit Skriptinterpretern arbeiten oder Teil von Skriptinterpretern sind. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden `IDebugEvent2` (das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die Schnittstelle zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn eine Quelldatei geöffnet werden muss. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugActivateDocumentEvent2`die Methoden von .

|Methoden|BESCHREIBUNG|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ruft das zu aktivierende Dokument ab.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ruft den Dokumentkontext ab, der die Position im Dokument beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Ein typisches Szenario, in dem diese Schnittstelle verwendet wird, ist, wenn ein Analysefehler im Skriptcode auf einer HTML-Seite auftritt, sendet das Skript DE diese Schnittstelle an das SDM, sodass das Dokument mit dem Analysefehler angezeigt werden kann.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
