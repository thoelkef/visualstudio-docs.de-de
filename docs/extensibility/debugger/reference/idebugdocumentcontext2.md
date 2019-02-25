---
title: Idebugdocumentcontext2 angegeben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3de9f48109590d6c59a46fd6451a750eecfbaa01
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678763"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Diese Schnittstelle stellt eine Position in einem Quelldokument für die Datei.

## <a name="syntax"></a>Syntax

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle als Teil der Unterstützung für den Codedebuggen. Zusätzlich zu einer Position im Quellcode stellt diese Schnittstelle Methoden zum Vergleichen von Kontexten, und Navigieren in einem Quellcodedokument bereit.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden für mehrere Schnittstellen, i. d. r. die [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) Schnittstellen zurückgeben, diese Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentContext2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ruft das Dokument, das Dokumentenkontext dieses enthält.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ruft den anzeigbaren Namen des Dokuments, das Dokumentenkontext dieses enthält.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Ruft eine Liste aller Code Kontexte, die mit diesem Dokumentenkontext verknüpft ist.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ruft die diesem Dokumentenkontext zugeordnete Sprache ab.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft die Datei Anweisungsbereich dieses Kontexts Dokument ab.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ruft die Datei Quellbereich dieses Kontexts Dokument ab.|
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Vergleicht diese Dokumentkontext in ein angegebenes Array von Dokument-Kontexten.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Verschiebt den Dokumentenkontext durch eine angegebene Anzahl von Anweisungen oder Zeilen an.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)