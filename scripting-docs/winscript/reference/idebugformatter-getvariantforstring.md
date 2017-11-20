---
title: IDebugFormatter::GetVariantForString | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9f783c8fe1864999e017ff348853df5464c93f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Gibt eine Variante, die die angegebene Zeichenfolge enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pwstrValue`  
 [in] Zeichenfolge, die in einem VARIANT zu speichern.  
  
 `pvar`  
 [out] VARIANT mit `pwstrValue`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt eine Variante, die mit der angegebenen Zeichenfolge zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFormatter-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)