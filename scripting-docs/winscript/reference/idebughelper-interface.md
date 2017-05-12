---
title: "IDebugHelper-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper-Schnittstelle"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper-Schnittstelle
Dient als Factory für Objektkataloge und einfache Verbindungspunkte.  Der Debug\- ProzessManager \(PDM\) implementiert diese Schnittstelle, die von Skriptmodule verwendet wird.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugHelper`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Gibt einen Eigenschaftenbrowser zurück, der eine VARIANTE umschließt.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Gibt einen Eigenschaftenbrowser, der eine VARIANTE umschließt zurück, und können benutzerdefinierte Konvertierung von VARIANTEN Werten zu, oder VARTYPE gibt in Zeichenfolgen ein.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Gibt eine Ereignisschnittstelle zurück, die ein angegebenes Objekt `IDispatch` umschließt.|