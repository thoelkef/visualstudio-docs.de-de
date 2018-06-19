---
title: IActiveScriptSiteWindow | Microsoft Docs
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
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725130"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Diese Schnittstelle wird implementiert, indem Hosts, die eine Benutzeroberfläche für das gleiche Objekt als unterstützen [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosts, die eine Benutzeroberfläche, z. B. Server, nicht unterstützen würden nicht implementieren die `IActiveScriptSiteWindow` Schnittstelle. Das Skriptmodul greift auf diese Schnittstelle durch den Aufruf `QueryInterface` aus `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Ruft das Fensterhandle, das als Besitzer eines Popupfensters bearbeiten können, die das Skriptmodul angezeigt werden muss.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Bewirkt, dass den Host zum Aktivieren oder deaktivieren das Hauptfenster als auch für alle nicht modale Dialogfelder.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)