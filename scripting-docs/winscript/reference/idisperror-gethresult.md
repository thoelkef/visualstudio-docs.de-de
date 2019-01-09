---
title: IDispError::GetHresult | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08020ea38c687cb0f69b1108935fd79802cc3120
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086280"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Ruft den Fehlercode aus der `IDispError` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phr`  
 [out] Gibt den Fehlercode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft den Fehlercode aus der `IDispError` Objekt.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)