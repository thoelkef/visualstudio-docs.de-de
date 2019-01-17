---
title: IActiveScriptSite::OnScriptError | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344563"
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