---
title: IDebugDocumentPositionOffset2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54a2e48960fa3103e5a927a4d2fac43e881ae072
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724455"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt eine Position in einer Quelldatei als ein Zeichenoffset dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Durch die IDE implementiert und von Debug-Engines.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentPositionOffset2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Ruft den Bereich für die aktuelle Dokumentposition ab.|  
  
## <a name="remarks"></a>Hinweise  
 Dies gibt die gleiche Informationen wie [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) aber in `char` offsets vom Anfang des Dokuments. Dies stellt das Dokument, wie es auf einem Datenträger, d. h. ein eindimensionales Array von Zeichen, anstatt der Zeilen- und Spaltennummer vorhanden wäre, der normalerweise zurückgegeben wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

