---
title: Iactivescriptsitewindow | Microsoft-Dokumentation
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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575898"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Diese Schnittstelle wird von Hosts implementiert, die eine Benutzeroberfläche für dasselbe Objekt wie [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) unterstützen. Hosts, die keine Benutzeroberfläche unterstützen, z. b. Server, implementieren die `IActiveScriptSiteWindow`-Schnittstelle nicht. Die Skript-Engine greift auf diese Schnittstelle zu, indem `QueryInterface` aus `IActiveScriptSite` aufgerufen wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Ruft das Fenster Handle ab, das als Besitzer eines Popup Fensters fungieren kann, das von der Skript-Engine angezeigt werden muss.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Bewirkt, dass der Host sein Hauptfenster sowie alle nicht modalem Dialogfelder aktiviert oder deaktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)