---
title: IDebugDocumentPosition2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4339be57479b54d9d3f040670e9ce161f7cd4715
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683180"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Diese Schnittstelle stellt eine abstrakte Position in einer Quelldatei dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio in der Regel implementiert. Ein Debugmodul (DE) würde auch diese Schnittstelle implementieren, wenn sie einen eigenen Quellcode bereitstellen muss (wie bei der DE implementiert die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird als Argument übergeben [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Es ebenfalls als Teil des angegeben wird eine [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (insbesondere eine [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur), die wiederum stammt von der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -Struktur wird verwendet, erstellen einen ausstehenden Haltepunkt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentPosition2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ruft ab, der Dateiname der Quelldatei, die Dokumentposition dieses enthält.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ruft das Containerdokument ab.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bestimmt, ob dieser Position in dem angegebenen Dokument enthalten ist.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ruft den Bereich für dieses Dokumentposition ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)