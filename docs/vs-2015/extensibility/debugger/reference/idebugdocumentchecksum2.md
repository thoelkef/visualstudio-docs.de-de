---
title: IDebugDocumentChecksum2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e6d3428b5091841f0229b146c9e086ceb208d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522014"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDocumentChecksum2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentchecksum2).  
  
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

