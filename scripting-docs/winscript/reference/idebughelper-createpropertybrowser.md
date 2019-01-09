---
title: IDebugHelper::CreatePropertyBrowser | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c3eedf9d6ed07b510d7912a5b28d23e0a1f05dda
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087749"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Gibt einen Eigenschaftenbrowser, der umschließt eine Variante zurück.  
  
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
 [in] Root-Variante zu durchsuchen.  
  
 `bstrName`  
 [in] Name für den Stamm.  
  
 `pdat`  
 [in] Thread auf dem Eigenschaften angefordert. Wenn dieser Parameter NULL ist, kein marshalling erfolgt.  
  
 `ppdob`  
 [out] Der Eigenschaftenbrowser.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser, der eine Variante umschließt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)