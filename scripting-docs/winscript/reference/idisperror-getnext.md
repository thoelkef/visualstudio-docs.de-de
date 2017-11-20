---
title: IDispError::GetNext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cbe4b044f2d3fb1d8ffb08565fc4093fbbe3ec7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Ruft den nächsten `IDispError` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppde`  
 [out] Gibt an, neben `IDispError` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft die nächste `IDispError` Objekt. Ist dies der letzte `IDispError` Objekt, diese Methode gibt NULL zurück.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)