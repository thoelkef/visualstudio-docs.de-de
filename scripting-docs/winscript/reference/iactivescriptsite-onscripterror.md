---
title: IActiveScriptSite::OnScriptError | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992605"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informiert den Host, dass ein Ausführungsfehler aufgetreten, während die Engine das Skript ausgeführt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pase`  
 [in] Adresse des des Fehlerobjekt [IActiveScriptError](../../winscript/reference/iactivescripterror.md) Schnittstelle. Ein Host kann diese Schnittstelle zum Abrufen von Informationen über den Ausführungsfehler verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` Wenn der Fehler ordnungsgemäß behandelt wurde, oder eine OLE Fehlercode, andernfalls definierte.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)