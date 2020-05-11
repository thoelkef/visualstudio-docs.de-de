---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731368"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Diese Schnittstelle wird verwendet, um Visual Studio über Änderungen am Quelldokument zu benachrichtigen, die vom Debugmodul bereitgestellt werden.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um Änderungen am Quellcode zu unterstützen. Diese Schnittstelle wird in der Regel für dasselbe Objekt implementiert, das die [IDebugDocument2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocument2.md) implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]erhält diese Schnittstelle durch einen <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Aufruf der Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird von einem <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> Aufruf der Methode abgerufen. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle wird durch Aufrufen der [QueryInterface-Methode](/cpp/atl/queryinterface) auf einer [IDebugDocument2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocument2.md) abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugDocumentTextEvents2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt das Debugpaket, dass Text in das Dokument eingefügt wurde.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt das Debugpaket, dass Text aus dem Dokument entfernt wurde.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt das Debugpaket, dass Text im Dokument ersetzt wurde.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt das Debugpaket, dass Textattribute im Dokument aktualisiert wurden.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt den Empfänger des Ereignisses, dass die Dokumentattribute aktualisiert wurden.|

## <a name="remarks"></a>Bemerkungen
 Nur Debug-Engines, die eigene Dokumente `IDebugDocumentTextEvent2` bereitstellen, würden die Schnittstelle nutzen. Ein Beispiel hierfür wäre ein Skriptdebugmodul. Beim Interpretieren von Skripts kann neuer Quellcode generiert werden, der in keiner Datenträgerdatei vorhanden ist und nur der DE bekannt ist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
