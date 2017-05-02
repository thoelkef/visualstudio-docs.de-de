---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
Gibt eine Zeichenfolge zurück, die den angegebenen VARTYPE\-Wert darstellt.  
  
## Syntax  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### Parameter  
 `vt`  
 \[in\] als Zeichenfolge darzustellen, VARTYPE.  
  
 `ptdescArrayType`  
 \[in\] Array von Strukturen, die Typen beschrieben werden.  
  
 `pbstr`  
 \[out\] Zeichenfolge, die `vt` darstellt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die Methode gibt eine Zeichenfolge zurück, die den angegebenen VARTYPE\-Wert darstellt.  
  
## Siehe auch  
 [IDebugFormatter\-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)