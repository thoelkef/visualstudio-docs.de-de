---
title: 'Iactivescriptsite:: getdocversionstring | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571135"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Ruft eine vom Host definierte Zeichenfolge ab, die die aktuelle Dokument Version eindeutig identifiziert. Wenn sich das zugehörige Dokument außerhalb des Bereichs des Windows-Skripts geändert hat (wie bei einer HTML-Seite, die mit Notepad bearbeitet wird), kann die Skript-Engine dies zusammen mit dem beibehaltenen Zustand speichern und eine erneute Kompilierung erzwingen, wenn das Skript das nächste Mal geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrVersionString`  
 vorgenommen Adresse der Host definierten Dokument Versions Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_NOTIMPL`, wenn diese Methode nicht unterstützt wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `E_NOTIMPL` zurückgegeben wird, sollte die Skript-Engine davon ausgehen, dass das Skript mit dem Dokument synchron ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)