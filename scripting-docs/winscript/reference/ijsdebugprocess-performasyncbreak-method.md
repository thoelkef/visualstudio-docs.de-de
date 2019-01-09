---
title: 'Ijsdebugprocess:: Performasyncbreak-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614bbfdde117ba223ca3f8f3d8b9b77c44c4393
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089140"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>IJsDebugProcess::PerformAsyncBreak-Methode
Setzt die Skript-Engine in den Unterbrechungsmodus, der bei der nächsten Skriptanweisung eine Unterbrechung veranlasst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `threadId`  
 [in] Die Thread-ID.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugProcess-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)