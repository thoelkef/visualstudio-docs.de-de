---
title: "IPerPropertyBrowsing2-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2-Schnittstelle"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2-Schnittstelle
Greift auf die Informationen in den Eigenschaftenseiten zu, die von einem Objekt bereitgestellt werden.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|`GetDisplayString`|Gibt eine Zeichenfolge zurück, die die angegebene Eigenschaft beschreibt.|  
|`MapPropertyToPage`|Gibt die CLSID der Eigenschaftenseite zurück, die Bearbeitung der angegebenen Eigenschaft zulässig.|  
|`GetPredefinedStrings`|Gibt ein Zeichenfolgenarray gezähltes \(`LPOLESTR` Zeiger\) die Beschreibungen der zulässigen Werte aufgeführt sind zurück, die die angegebene Eigenschaft annehmen kann.|  
|`SetPredefinedValue`|Legt den Wert der Eigenschaft auf den vordefinierten Wert fest, der durch das Token `dwCookie.` identifiziert wird|  
  
## Anforderungen  
 Header: dbgprop.h