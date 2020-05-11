---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717269"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Diese Schnittstelle zählt die Codekontexte auf, die der Debugsitzung oder einem bestimmten Programm oder Dokument zugeordnet sind.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Liste von Codekontexten für eine bestimmte Textposition in einem Programm oder eine Liste von Codekontexten für einen bestimmten Dokumentkontext darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) auf, um diese Schnittstelle abzurufen, die eine Liste von Codekontexten für eine bestimmte Textposition im Quelldokument eines Programms darstellt.

 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) auf, um diese Schnittstelle abzurufen, die eine Liste aller Codekontexte in einem bestimmten Quelldokument darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugCodeContexts2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Ruft eine angegebene Anzahl von Codekontexten in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Überspringt eine angegebene Anzahl von Codekontexten in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ruft die Anzahl der Codekontexte in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) auf, um eine Liste von Codekontexten aufzufüllen, aus denen der Benutzer auswählen kann, wenn er die nächste Anweisung festlegt oder die Demontage für eine Quelldatei anzeigt. Mehrere Codekontexte können auftreten, z. B. wenn mehrere Instanzen einer C++-Vorlage vorhanden sind.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
