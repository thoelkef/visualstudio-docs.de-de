---
title: 'Ijsdebugbreakpoint:: Getdocumentposition-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146eb26c887cd24d1eb7af858535fcecac62b41d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583144"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition-Methode
Gibt die Position der Anweisung zurück, wo der Haltepunkt gebunden wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDocumentId`  
 [out] Eindeutige ID für ein Quelldokument (Zeiger auf "IDebugDocumentText").  
  
 `pCharacterOffset`  
 [out] Das nullbasierte Zeichenoffset vom Anfang des Skripts.  
  
 `pStatementCharCount`  
 [out] Die Länge der aktuellen Anweisung, die am "*pCharacterOffset" beginnt, in Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugBreakPoint-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)