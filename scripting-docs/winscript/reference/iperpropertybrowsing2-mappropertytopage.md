---
title: IPerPropertyBrowsing2::MapPropertyToPage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605c1178ca01c6c55ef170bb4650625bec21c0f8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087190"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Gibt die CLSID der Eigenschaftenseite, die verwendet werden kann, zum Bearbeiten dieser Eigenschaft zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Dispatchbezeichner von der gewünschten Eigenschaft.  
  
 `pClsidPropPage`  
 [out] Zeiger auf die CLSID, identifizieren die Eigenschaftenseite der Eigenschaft zugeordnet. Wenn diese Methode schlägt fehl, *`pClsidPropPage` auf CLSID_NULL festgelegt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)