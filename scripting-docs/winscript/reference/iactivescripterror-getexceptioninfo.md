---
title: 'Iactivescripterror:: getexceptioninfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2f776a5f1a60b1280ab1f133ead04fb275782e5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576945"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Ruft Informationen zu einem Fehler ab, der aufgetreten ist, während die Skript-Engine ein Skript ausgeführt hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pexcepinfo`  
 vorgenommen Adresse einer `EXCEPINFO`-Struktur, die Fehlerinformationen empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)