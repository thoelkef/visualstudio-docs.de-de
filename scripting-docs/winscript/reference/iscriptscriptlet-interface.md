---
title: "IScriptScriptlet-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptScriptlet-Schnittstelle"
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptScriptlet-Schnittstelle
Ein Objekt, das die `IScriptScriptlet`\-Schnittstelle implementiert, stellt ein Ereignishandlerskripts dar.  
  
 Zusätzlich zu den von `IScriptEntry` geerbten Methoden macht die `IScriptScriptlet`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Gibt den Namen des Ereignisses zurück, das mit dem Skriptlet zugeordnet ist.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Gibt den einfachen Ereignisnamen zurück, der mit einem Skriptlet zugeordnet ist.  Dies ist ein Einwortname, der keine Leerzeichen enthält.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Gibt den letzten Bezeichner im vollqualifizierten Namen des Objekthosts eines Skriptlets zurück.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Legt den Namen des Ereignisses fest, das mit dem Skriptlet zugeordnet ist.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Legt den einfachen Ereignisnamen fest, der mit einem Skriptlet zugeordnet ist.  Dies ist ein Einwortname, der keine Leerzeichen enthält.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Legt den letzten Bezeichner im vollqualifizierten Namen des Objekthosts eines Skriptlets fest.|  
  
## Siehe auch  
 [Active Script\-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)