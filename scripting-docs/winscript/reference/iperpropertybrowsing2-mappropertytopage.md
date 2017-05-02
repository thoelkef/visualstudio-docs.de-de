---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
Gibt die CLSID der Eigenschaftenseite zurück, die verwendet werden kann, um die Eigenschaft zu bearbeiten.  
  
## Syntax  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### Parameter  
 `dispid`  
 \[in\] Dispatchbezeichner in der relevanten Eigenschaft.  
  
 `pClsidPropPage`  
 \[out\] Zeiger auf CLSID, das die Eigenschaftenseite zugeordnet mit der Eigenschaft identifiziert.  Wenn diese Methode fehlschlägt, \*`pClsidPropPage` wird zu CLSID\_NULL festgelegt.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IPerPropertyBrowsing2\-Schnittstelle](../../winscript/reference/iperpropertybrowsing2-interface-1.md)