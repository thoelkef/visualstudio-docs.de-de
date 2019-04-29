---
title: IActiveScriptSiteWindow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3691a874121c00dcccc69958eb5746a2c1d78122
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992025"
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