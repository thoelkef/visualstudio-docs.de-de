---
title: IActiveScriptSiteWindow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a160b17f4a46237ab78b378664a046fe8a0e7d4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345720"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Diese Schnittstelle wird implementiert von Hosts, die eine Benutzeroberfläche auf dasselbe Objekt wie unterstützen [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosts, die nicht über eine Benutzeroberfläche, z. B. Server, unterstützen würde nicht implementiert. die `IActiveScriptSiteWindow` Schnittstelle. Die Skript-Engine greift auf diese Schnittstelle durch den Aufruf `QueryInterface` aus `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Ruft das Fensterhandle, das als Besitzer eines Popupfensters fungieren kann, die die Skript-Engine angezeigt werden muss.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Bewirkt, dass den Host zum Aktivieren oder deaktivieren das Hauptfenster als auch für alle Dialogfelder ohne Modus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)