---
title: 'Idebughelper:: kreatepropertybrowserex | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576497"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Gibt einen Eigenschaften Browser zurück, der eine Variante umschließt und die benutzerdefinierte Konvertierung von Variant-Werten oder VarType-Typen in Zeichen folgen ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 in Objekt, das benutzerdefinierte Formatierung für Varianten bereitstellt.  
  
 `ppdob`  
 vorgenommen Der Eigenschaften Browser.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Eigenschaften Browser zurück, der eine Variante umschließt und die benutzerdefinierte Konvertierung von Variant-Werten oder VarType-Typen in Zeichen folgen ermöglicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebughelper::](../../winscript/reference/idebughelper-createpropertybrowser.md)   der  
 [Idebughelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)    
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)