---
title: IDebugDocumentTextEvents2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e24568d307db694d30a5e87630f47f764a036427
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681724"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Diese Schnittstelle wird verwendet, um Visual Studio zu Änderungen bei Quelldokument zu benachrichtigen, die von der Debug-Engine bereitgestellt werden.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um Änderungen an den Quellcode zu unterstützen. Diese Schnittstelle wird in der Regel implementiert, für das gleiche Objekt, das implementiert die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ruft diese Schnittstelle durch einen Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird von einem Aufruf von Abrufen der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle wird abrufen durch Aufrufen der [QueryInterface](/cpp/atl/queryinterface) Methode für ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentTextEvents2`.

|Methode|Beschreibung|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt dem debugpaket an, dass Text in das Dokument eingefügt wurde.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt dem debugpaket an, dass Text aus dem Dokument entfernt wurde.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt dem debugpaket, dass im Dokument Text ersetzt wurde.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt dem debugpaket, Text-Attribute im Dokument aktualisiert wurden.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt Empfänger des Ereignisses, dass die Attribute des Dokuments aktualisiert wurden.|

## <a name="remarks"></a>Hinweise
 Nur Debug-Engines, die ihre eigenen Dokumente angeben nutzen würden die `IDebugDocumentTextEvent2` Schnittstelle. Ein Beispiel hierfür wäre eine Skript DebugEngine. Beim Interpretieren von Skripts, kann neue Quellcode generiert werden, die nicht in jeder Datenträgerdatei vorhanden ist, und wird nur für das DE bezeichnet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)