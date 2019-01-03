---
title: IDebugDocumentChecksum2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 784c8cd4bf762e97b69c6a88ae99701dc993efc5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921678"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Stellt eine Prüfsumme für eine Debug-Dokument und ermöglicht die Prüfsumme zwischen Komponenten übergeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle implementiert werden kann, von keiner Komponente, die verfügbar macht die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle. Allerdings ist es hauptsächlich durch Debugmodule implementiert, damit die Prüfsumme, eingebettet in eine Symboldatei (*.pdb) wieder an der IDE übergeben und beim Suchen einer Quelle verwendet werden kann.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentChecksum2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Ruft die Prüfsumme und Algorithmus Dokumentbezeichner erhalten die maximale Anzahl von Bytes, die ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll