---
title: IDebugFormatter::GetStringForVariant | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a7b2eefb69435333509c4b9cda986cc75e431f73
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097447"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Gibt eine Zeichenfolge, die den angegebenen VARIANT-Wert darstellt.  
  
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
 [in] Variant-Wert als Zeichenfolge dargestellt.  
  
 `nRadix`  
 [in] Basis für numerische Werte verwendet.  
  
 `pbstrValue`  
 [out] Zeichenfolgendarstellung `pvar`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt eine Zeichenfolge, die den angegebenen variant-Wert darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFormatter-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)