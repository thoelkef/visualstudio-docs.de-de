---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
Gibt einen Eigenschaftenbrowser zurück, der eine VARIANTE umschließt und benutzerdefinierte Konvertierung von VARIANTEN Werte zulässt, oder VARTYPE in Zeichenfolgen eingibt.  
  
## Syntax  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Parameter  
 `pvar`  
 \[in\] zu suchen Stammvariante.  
  
 `bstrName`  
 \[in\] Name, Seitenstamm zu geben.  
  
 `pdat`  
 \[in\] einer Tabelle in der, um Eigenschaften anfordern.  Wenn dieser Parameter NULL ist, wird kein Marshalling ausgeführt.  
  
 `pdf`  
 \[in\] wenden Sie ein, das benutzerdefinierte Formatierung für Varianten bereitstellt.  
  
 `ppdob`  
 \[out\] Der Eigenschaftenbrowser.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser zurück, der eine VARIANTE umschließt und benutzerdefinierte Konvertierung von VARIANTEN Werte zulässt, oder VARTYPE in Zeichenfolgen eingibt.  
  
## Siehe auch  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper\-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)