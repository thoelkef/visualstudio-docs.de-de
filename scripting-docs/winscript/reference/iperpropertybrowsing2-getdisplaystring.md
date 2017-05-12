---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
Ruft eine Zeichenfolge an Typen angezeigt, die nicht der zurückgegebene Text ist ein Name grundsätzlich sichtbar sind, der die Eigenschaft werden und kann in der Benutzeroberfläche des Aufrufers angezeigt werden.  
  
## Syntax  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### Parameter  
 `dispid`  
 \[in\] Dispatchbezeichner in der Eigenschaft, deren Anzeigename angefordert wird.  
  
 `pBstr`  
 \[out\] Zeiger auf `BSTR`, das den Anzeigenamen für die Eigenschaft identifiziert durch `dispID` enthält.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Hinweise  
 Die zurückgegebene Zeichenfolge ist kein gültiger Wert der Eigenschaft.  Es ist nur eine Zeichenfolgenanzeige der Eigenschaft.  
  
## Siehe auch  
 [IPerPropertyBrowsing2\-Schnittstelle](../../winscript/reference/iperpropertybrowsing2-interface-1.md)