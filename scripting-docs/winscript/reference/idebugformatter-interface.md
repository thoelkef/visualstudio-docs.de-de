---
title: "IDebugFormatter-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugFormatter-Schnittstelle"
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter-Schnittstelle
Ermöglicht einer Sprache oder ein IDE, um die Konvertierung zwischen VARIANTEN Werten oder VARTYPE\-Typen und Zeichenfolgen anzupassen.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugFormatter`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Gibt eine Zeichenfolge zurück, die den angegebenen VARIANTEN Wert darstellt.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Gibt eine VARIANTE zurück, die die angegebene Zeichenfolge enthält.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Gibt eine Zeichenfolge zurück, die den angegebenen VARTYPE\-Wert darstellt.|