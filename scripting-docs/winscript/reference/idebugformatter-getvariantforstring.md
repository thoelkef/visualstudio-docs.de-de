---
title: IDebugFormatter::GetVariantForString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea6cd1f77481282700de492e2857046044a04e2a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155380"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Gibt eine Variante, die die angegebene Zeichenfolge enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pwstrValue`  
 [in] Zeichenfolge, die in einer Variante gespeichert.  
  
 `pvar`  
 [out] VARIANT mit `pwstrValue`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt eine Variante, die die angegebene Zeichenfolge enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFormatter-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)