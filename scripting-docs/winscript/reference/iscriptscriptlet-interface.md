---
title: IScriptScriptlet-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3fa3253997d3a09a7170f3795bf8a7bbf8a182c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet-Schnittstelle
Ein Objekt, implementiert die `IScriptScriptlet` Schnittstelle stellt eine Ereignishandlerskripts dar.  
  
 Zusätzlich zu den von geerbten Methoden `IScriptEntry`, `IScriptScriptlet` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Gibt den Namen des Ereignisses, die dem Scriptlet zugeordnet ist.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Gibt den einfachen Ereignisname, der eine Scriptlet zugeordnet ist. Dies ist ein einzelnes Wort, der keine Leerzeichen enthalten.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Gibt den letzten Bezeichner in den vollqualifizierten Namen des Hosts für eine Scriptlet-Objekt zurück.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Legt den Namen des Ereignisses, die dem Scriptlet zugeordnet ist.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Legt den einfachen Namen, der dem Scriptlet zugeordnet ist. Dies ist ein einzelnes Wort, der keine Leerzeichen enthalten.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Legt den letzten Bezeichner in den vollqualifizierten Namen des Hosts für eine Scriptlet-Objekt fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)