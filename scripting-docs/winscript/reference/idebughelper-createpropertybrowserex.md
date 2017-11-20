---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Gibt einen Eigenschaftenbrowser, der dient als Wrapper für eine Variante und ermöglicht eine benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Thread für die Eigenschaften anfordern. Wenn dieser Parameter NULL ist, wird kein marshalling ausgeführt.  
  
 `pdf`  
 [in] Objekt, das für Varianten stellt benutzerdefinierte Formatierung.  
  
 `ppdob`  
 [out] Eigenschaftenbrowser.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser, der eine Variante umschließt und für die benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen zulässt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)