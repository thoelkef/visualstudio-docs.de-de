---
title: "IDebugFormatter::GetStringForVariant | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVariant"
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVariant
Gibt eine Zeichenfolge zurück, die den angegebenen VARIANTEN Wert darstellt.  
  
## Syntax  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### Parameter  
 `pvar`  
 \[in\] als Zeichenfolge darzustellen, VARIANTE.  
  
 `nRadix`  
 \[in\] für numerische Werte zu verwenden, Basis.  
  
 `pbstrValue`  
 \[out\] Zeichenfolge, die `pvar` darstellt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt eine Zeichenfolge zurück, die den angegebenen varianten Wert darstellt.  
  
## Siehe auch  
 [IDebugFormatter\-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)