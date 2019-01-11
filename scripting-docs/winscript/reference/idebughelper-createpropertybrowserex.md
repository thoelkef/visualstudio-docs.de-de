---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c3590fe05ef82f094dd5706f9f527b247d95eda8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097733"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Gibt einen Eigenschaftenbrowser, der eine Variante umschließt und ermöglicht die benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen zurück.  
  
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
 [in] Root-Variante zu durchsuchen.  
  
 `bstrName`  
 [in] Name für den Stamm.  
  
 `pdat`  
 [in] Thread auf dem Eigenschaften angefordert. Wenn dieser Parameter NULL ist, kein marshalling erfolgt.  
  
 `pdf`  
 [in] Objekt, das für Varianten stellt benutzerdefinierte Formatierung.  
  
 `ppdob`  
 [out] Der Eigenschaftenbrowser.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser, der eine Variante umschließt und ermöglicht die benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)