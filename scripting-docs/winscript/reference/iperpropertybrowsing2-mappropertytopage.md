---
title: IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79b8d7cb9e1c8a9f79cdddc4f8d3404ff7a2036c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Gibt die CLSID der Eigenschaftenseite, die zum Bearbeiten dieser Eigenschaft verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Dispatchbezeichner von der gewünschten Eigenschaft.  
  
 `pClsidPropPage`  
 [out] Ein Zeiger auf die CLSID, identifizieren die Eigenschaftenseite der Eigenschaft zugeordnet. Wenn diese Methode fehlschlägt, *`pClsidPropPage` auf CLSID_NULL festgelegt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)