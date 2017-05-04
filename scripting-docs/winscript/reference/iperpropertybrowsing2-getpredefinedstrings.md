---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
Ermöglicht dem Aufrufer, um ein Listenfeld mit einem gezählten Array Zeichenfolgenzeigern auszufüllen, die mögliche Werte für diese Eigenschaft darstellen.  
  
## Syntax  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### Parameter  
 `dispid`  
 \[in\] Dispatchbezeichner in der Eigenschaft, für die der Aufrufer die Zeichenfolgenliste anfordert.  
  
 `pCaStrings`  
 \[out\] Zeiger auf eine vom Aufrufer reservierten, gezählten Arraystruktur, die die Elementanzahl und die Adresse eines Arrays Methode\-zugeordneten Zeichenfolgenzeiger enthält.  Wenn die Methode fehlschlägt, wird kein Speicher belegt, und der Inhalt der Struktur ist nicht definiert.  
  
 `pCaCookies`  
 \[out\] Zeiger auf die vom Aufrufer reservierten, gezählten Arraystruktur, die die Elementanzahl und die Adresse eines Methode\-zugeordneten Arrays Dworde enthält.  Wenn die Methode fehlschlägt, wird kein Speicher belegt, und der Inhalt der Struktur ist nicht definiert.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IPerPropertyBrowsing2\-Schnittstelle](../../winscript/reference/iperpropertybrowsing2-interface-1.md)