---
title: 'IPerPropertyBrowsing2:: mappropertytopage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e9e3f821d9e02be567f970d8db1c238ee5cebd29
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577118"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Gibt die CLSID der Eigenschaften Seite zurück, die zum Bearbeiten dieser Eigenschaft verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 in Dispatchbezeichner der Eigenschaft, die von Interesse ist.  
  
 `pClsidPropPage`  
 vorgenommen Ein Zeiger auf die CLSID, die die Eigenschaften Seite identifiziert, die der Eigenschaft zugeordnet ist. Wenn diese Methode fehlschlägt, ist * `pClsidPropPage` auf CLSID_NULL festgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)