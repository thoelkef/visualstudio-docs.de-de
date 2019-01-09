---
title: IActiveScriptError::GetExceptionInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf48362686a05a958a067cffa1015ffe2d58cecc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096225"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Ruft Informationen zu einem Fehler, der aufgetreten sind, während die Skript-Engine ein Skript ausgeführt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pexcepinfo`  
 [out] Adresse von einem `EXCEPINFO` Struktur, die Informationen empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` , wenn ein Fehler aufgetreten ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)