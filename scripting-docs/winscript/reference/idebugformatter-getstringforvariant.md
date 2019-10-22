---
title: 'Idebugformatter:: getstringforvariant | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576370"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Gibt eine Zeichenfolge zurück, die den angegebenen Variant-Wert darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvar`  
 in Variant, die als Zeichenfolge dargestellt werden soll.  
  
 `nRadix`  
 in Für numerische Werte zu verwendende Radix-Werte.  
  
 `pbstrValue`  
 vorgenommen Zeichenfolge, die `pvar` darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt eine Zeichenfolge zurück, die den angegebenen Variant-Wert darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFormatter-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)