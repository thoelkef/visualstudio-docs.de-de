---
title: IScriptScriptlet-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c11aada6b8c39c7dd5f0b2a6b30cdd837aa0edda
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151257"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet-Schnittstelle
Ein Objekt, implementiert die `IScriptScriptlet` Schnittstelle repräsentiert ein Ereignis-Handler-Skript.  
  
 Zusätzlich zu den von geerbten Methoden `IScriptEntry`, `IScriptScriptlet` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Gibt den Namen des Ereignisses, das das Scriptlet zugeordnet ist.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Gibt den einfachen Namen, der dem Scriptlet zugeordnet ist. Dies ist ein Name einem Wort, die keine Leerzeichen enthalten.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Gibt den letzten Bezeichner in den vollqualifizierten Namen des Hosts des Scriptlet-Objekt zurück.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Legt den Namen des Ereignisses, das das Scriptlet zugeordnet ist.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Legt den einfachen Namen, der dem Scriptlet zugeordnet ist. Dies ist ein Name einem Wort, die keine Leerzeichen enthalten.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Legt den letzten Bezeichner in den vollqualifizierten Namen des Hosts des Scriptlet-Objekt fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)