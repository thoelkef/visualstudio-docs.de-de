---
title: 'Iactivescriptsite:: onscripterror | Microsoft-Dokumentation'
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
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570269"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Benachrichtigt den Host, dass während der Ausführung des Skripts durch die Engine ein Ausführungsfehler aufgetreten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pase`  
 in Adresse der [iactivescripterror](../../winscript/reference/iactivescripterror.md) -Schnittstelle des Fehler Objekts. Ein Host kann diese Schnittstelle zum Abrufen von Informationen über den Ausführungsfehler verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn der Fehler ordnungsgemäß behandelt wurde, andernfalls einen Fehlercode, der von OLE definiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)