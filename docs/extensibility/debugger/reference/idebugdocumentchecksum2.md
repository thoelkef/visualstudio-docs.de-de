---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731897"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Stellt eine Prüfsumme für ein Debugdokument dar und ermöglicht das Übergeben der Prüfsumme zwischen Komponenten.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle kann von jeder Komponente implementiert werden, die die [IDebugDocumentContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) verfügbar macht. Sie wird jedoch hauptsächlich von Debug-Engines implementiert, sodass die in eine Symboldatei (*.pdb) eingebettete Prüfsumme an die IDE zurücküberwiesen und beim Suchen einer Quelle verwendet werden kann.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugDocumentChecksum2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Ruft die Dokumentprüfsumme und den Algorithmusbezeichner anhand der maximal zu verwendenden Anzahl von Bytes ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
