---
title: 'Idisperror:: GetNext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573104"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Ruft das nächste `IDispError` Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppde`  
 vorgenommen Gibt das nächste `IDispError` Objekt an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft das nächste `IDispError` Objekt ab. Wenn dies das letzte `IDispError` Objekt ist, gibt diese Methode NULL zurück.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)