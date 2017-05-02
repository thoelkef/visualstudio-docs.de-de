---
title: "IScriptEntry-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry-Schnittstelle"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry-Schnittstelle
Ein Objekt, das die `IScriptEntry`\-Schnittstelle implementiert, stellt entweder einen Skriptblock oder ein Funktionsobjekt dar.  
  
 Zusätzlich zu den von `IScriptNode` geerbten Methoden macht die `IScriptEntry`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Gibt den Text zurück, der dem Text eines `IScriptEntry` Skriptblocks, des Funktionsblocks oder des Skriptlets entspricht.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Gibt den Elementnamen zurück, der ein `IScriptEntry`\-Objekt identifiziert.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Für Einträge, die ein einzelnes Objekt darstellen \(wie eine Funktion\), den Namen des Objekts.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Gibt die Anfangsposition und die Länge eines Eintrags zurück.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Gibt Typinformationen für ein `IScriptEntry`\-Funktionsobjekt zurück.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Gibt den Text, der einem `IScriptEntry` Skriptblock entspricht, oder den Quellcode zurück, der in einem `IScriptScriptlet`\-Ereignishandler enthalten ist.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Legt den Text fest, der im Text eines `IScriptEntry` Skriptblocks oder des `IScriptScriptlet` Skriptlets ist.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Legt den Elementnamen fest, der ein `IScriptEntry`\-Objekt identifiziert.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Für Einträge, die ein einzelnes Objekt darstellen \(wie eine Funktion\), wird der Name des Objekts.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Legt Typinformationen für ein `IScriptEntry`\-Funktionsobjekt fest.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Legt den Text, der einem `IScriptEntry` Skriptblock entspricht, oder den Quellcode fest, der in einem `IScriptScriptlet`\-Ereignishandler enthalten ist.|  
  
## Siehe auch  
 [Active Script\-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)