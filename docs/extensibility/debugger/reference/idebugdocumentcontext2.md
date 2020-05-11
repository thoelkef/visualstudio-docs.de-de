---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731729"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Diese Schnittstelle stellt eine Position in einem Quelldateidokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für das Debuggen auf Quellcodeebene. Zusätzlich zu einer Position im Quellcode stellt diese Schnittstelle Methoden zum Vergleichen von Kontexten und Navigieren durch ein Quellcodedokument bereit.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Methoden auf mehreren Schnittstellen, in der Regel die [GetDocumentContext-](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und [GetDocumentContext-Schnittstellen,](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugDocumentContext2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ruft das Dokument ab, das diesen Dokumentkontext enthält.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ruft den angezeigten Namen des Dokuments ab, das diesen Dokumentkontext enthält.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Ruft eine Liste aller Codekontexte ab, die diesem Dokumentkontext zugeordnet sind.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ruft die Sprache ab, die diesem Dokumentkontext zugeordnet ist.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Dateianweisungsbereich dieses Dokumentkontexts ab.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ruft den Dateiquellbereich dieses Dokumentkontexts ab.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Vergleicht diesen Dokumentkontext mit einem bestimmten Array von Dokumentkontexten.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Verschiebt den Dokumentkontext um eine bestimmte Anzahl von Anweisungen oder Zeilen.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
