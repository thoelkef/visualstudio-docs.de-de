---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 50fbee2dbdb30873c97f1ca465d99161add90a19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Stellt eine Prüfsumme für eine Debug-Dokument dar und ermöglicht es die Prüfsumme zwischen Komponenten übergeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle kann von keiner Komponente, die verfügbar macht implementiert werden die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle. Allerdings ist es hauptsächlich durch Debugmodule implementiert, damit die Prüfsumme, eingebettet in eine Symboldatei (.pdb) wieder an der IDE übergeben und beim Suchen einer Quelle verwendet werden kann.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentChecksum2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Ruft die Prüfsumme und Algorithmus Dokumentbezeichner erhält die maximale Anzahl von Bytes zu verwenden.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll