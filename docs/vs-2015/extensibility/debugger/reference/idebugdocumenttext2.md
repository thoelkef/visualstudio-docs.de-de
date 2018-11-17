---
title: IDebugDocumentText2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85b5d9e78af9e4e49b3a985ca00ffad102e6b53d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728848"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Textdokument.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul (DE) implementiert diese Schnittstelle auf, wenn der Quellcode, die, den Sie zur Verfügung stellen muss, im Text-Format ist. Da dies der häufigste Fall ist, wenn eine bereitgestellten Kompatibilitätsrichtlinie implementiert die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle, sie sollten auch implementieren die `IDebugDocumentText2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwenden der `QueryInterface` -Methode dieser Schnittstelle vom Abrufen einer `IDebugDocument2` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die `IDebugDocument2` Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Ruft die Größe des Texts an dieser Position im Dokument ab.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Ruft den Text aus der angegebenen Position im Dokument ab.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Objekt, das diese Schnittstelle implementiert, muss auch implementieren die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle, die stellt die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> eine Schnittstelle für ein [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) Objekt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

