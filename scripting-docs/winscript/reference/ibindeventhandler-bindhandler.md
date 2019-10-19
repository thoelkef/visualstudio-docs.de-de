---
title: 'Ibindeventhandler:: bindhandler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 160020832509c9fb2aa95c095148127228a92e17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572571"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Bindet ein Ereignis an ein-Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrEvent`  
 in Gibt das Ereignis an, das behandelt werden soll.  
  
 `pdisp`  
 in Gibt das-Objekt an, das das Ereignis behandelt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bindet ein Ereignis an ein-Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IBindEventHandler-Schnittstelle](../../winscript/reference/ibindeventhandler-interface.md)