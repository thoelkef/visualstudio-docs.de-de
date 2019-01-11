---
title: 'Ijsdebugframe:: Getdocumentpositionwithname-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6333f9c52c3ab4e0cd01c34f5e5228721aa55b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093833"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName-Methode
Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDocumentName`  
 [out] Für statische Skripts, eine zu dokumentieren URL. Für dynamische Skripts wird ein Name, der den Typ des Skripts enthält (beispielsweise Auswertungscode, Funktionscode, usw.) zurückgegeben.  
  
 `pLine`  
 [out] 1-basierende Zeilenposition innerhalb des Dokuments.  
  
 `pColumn`  
 [out] 1-basierende Zeilenposition innerhalb des Dokuments.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)