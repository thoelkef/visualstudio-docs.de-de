---
title: 'Ijsdebugframe:: GetStackRange-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574040"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange-Methode
Gibt den Bereich der absoluten Adresse des logischen JavaScript-Stapelrahmens zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStart`  
 [out] Unterster Stapelzeiger des Frames.  
  
 `pEnd`  
 [out] Oberster Stapelzeiger des Frames.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist für die Zusammenführung überlappender Stapelüberwachungen nützlich, die aus mehreren Laufzeiten erfasst wird. Die Start-und endstapel Zeiger können mehrere physische Computer Stapel Rahmen (für interpretierte JavaScript-Lauf Zeitrahmen) umfassen. Start > Ende, wenn der Stapel von der hohen zu niedrigen Adresse wächst.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)