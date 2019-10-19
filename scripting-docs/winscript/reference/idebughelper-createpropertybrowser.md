---
title: 'Idebughelper:: kreatepropertybrowser | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562501"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Gibt einen Eigenschaften Browser zurück, der eine Variante umschließt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvar`  
 in Stamm Variante zum Durchsuchen.  
  
 `bstrName`  
 in Der Name, der dem Stamm zugewiesen werden soll.  
  
 `pdat`  
 in Der Thread, für den Eigenschaften angefordert werden sollen. Wenn dieser Parameter NULL ist, wird kein Marshalling ausgeführt.  
  
 `ppdob`  
 vorgenommen Der Eigenschaften Browser.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Eigenschaften Browser zurück, der eine Variante umschließt.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebughelper:: kreatepropertybrowserex](../../winscript/reference/idebughelper-createpropertybrowserex.md)    
 [Idebughelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)    
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)