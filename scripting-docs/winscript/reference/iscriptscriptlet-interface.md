---
title: Iscriptscriptlet-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571889"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet-Schnittstelle
Ein Objekt, das die `IScriptScriptlet`-Schnittstelle implementiert, stellt ein Ereignishandler-Skript dar.  
  
 Zusätzlich zu den Methoden, die von `IScriptEntry` geerbt werden, macht die `IScriptScriptlet`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Gibt den Namen des Ereignisses zurück, das mit dem Scriptlet verknüpft ist.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Gibt den einfachen Ereignis Namen zurück, der mit einem Scriptlet verknüpft ist. Dies ist ein einzelner Wort Name, der keine Leerzeichen enthält.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Gibt den letzten Bezeichner im voll qualifizierten Namen des Objekt Hosts eines Scriptlets zurück.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Legt den Namen des Ereignisses fest, das dem Scriptlet zugeordnet ist.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Legt den einfachen Ereignis Namen fest, der einem Scriptlet zugeordnet ist. Dies ist ein einzelner Wort Name, der keine Leerzeichen enthält.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Legt den letzten Bezeichner im voll qualifizierten Namen des Objekt Hosts eines Scriptlets fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)