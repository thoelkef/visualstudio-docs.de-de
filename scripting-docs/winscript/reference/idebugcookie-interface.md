---
title: Idebugcookie-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573194"
---
# <a name="idebugcookie-interface"></a>IDebugCookie-Schnittstelle
Ermöglicht das Festlegen des debugcookies für die Verwendung mit der `IMachineDebugManagerCookie`-Schnittstelle. Weitere Informationen finden Sie unter [imachinedebugmanagercookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md). Diese Schnittstelle wird vom Process Debug Manager (PDM) implementiert und von Skript Debugger verwendet.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IDebugCookie`-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Legt das debuganwendungscookie fest.|  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManagerCookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)