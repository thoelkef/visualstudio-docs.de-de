---
title: 'Ijsdebugbreakpoint:: Getdocumentposition-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2d92a58dabe76e391d55996e511409fb63c9d671
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097668"
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
 [out] Die Länge der aktuellen Anweisung, die am *pCharacterOffset beginnt, in Zeichen.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugBreakPoint-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)