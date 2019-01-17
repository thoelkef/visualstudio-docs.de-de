---
title: IScriptScriptlet-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a3b7c4af7769a1a2851e9be4e2639a324a3c06fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345915"
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