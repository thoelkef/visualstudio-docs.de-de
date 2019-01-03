---
title: IDebugDocumentText2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cae0bfefe4ab39d42f9cc67080d17394b1a1418b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838423"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
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