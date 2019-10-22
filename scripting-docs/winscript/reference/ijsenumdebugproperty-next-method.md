---
title: 'Ijsenaufdebugproperty:: Next-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48c4506d783093395b2d88b7a71d56e3a89d24e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573987"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next-Methode
Liest die Eigenschaften für dieses Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `count`  
 [in] Die Anzahl der zu lesenden Eigenschaften.  
  
 `ppDebugProperty`  
 [out] Objekt, das den Eigenschaftenbrowser darstellt.  
  
 `pActualCount`  
 [out] Die tatsächliche Anzahl von Eigenschaften des Objekts.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsEnumDebugProperty-Schnittstelle](../../winscript/reference/ijsenumdebugproperty-interface.md)