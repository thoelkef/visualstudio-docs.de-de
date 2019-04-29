---
title: Active Script-Konstanten, Enumerationen und Fehlercodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090b494e904fbef1c0d3d8b380f7a184a6042788
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953997"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Konstanten, Enumerationen und Fehlercodes für Active Script
Dieser Abschnitt beschreibt die Enumerationen und Fehlercodes, die in Windows Scripting-Engines verwendet werden.  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTTHREADID-Konstanten](../../winscript/reference/scriptthreadid-constants.md)|Gibt den Typ des Threads.|  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Dient zum angeben, und zwar unabhängig davon, ob die Skript-Engine aufbewahrt werden sollen voll funktionsfähig, wenn ausstehende Verweise vorhanden sind.|  
  
## <a name="enumerations"></a>Enumerationen  
  
|Enumeration|Beschreibung|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE-Enumeration](../../winscript/reference/scriptgctype-enumeration.md)|Der Typ der Garbagecollection ausführen.|  
|[SCRIPTLANGUAGEVERSION-Enumeration](../../winscript/reference/scriptlanguageversion-enumeration.md)|Gibt die möglichen Versionen Skripterstellung.|  
|[SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md)|Gibt den Zustand einer Skript-Engine.|  
|||  
|[SCRIPTTHREADSTATE-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md)|Gibt den Zustand eines Threads in einer Skript-Engine an.|  
|[SCRIPTTRACEINFO-Enumeration](../../winscript/reference/scripttraceinfo-enumeration.md)|Stellt das Skriptereignis, das Ablaufverfolgung ausgeführt wird. Verwendet die [iactivescriptsitetraceinfo:: Sendscripttraceinfo-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md)|Stellt die Möglichkeit, dass das UI-Steuerelement behandelt werden soll.|  
|[SCRIPTUICITEM-Enumeration](../../winscript/reference/scriptuicitem-enumeration.md)|Stellt den Typ des UI-Elements dar. Verwendet die [iactivescriptsiteuicontrol:: Getuibehavior-Methode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Fehlercodes  
  
|Fehlercode|Beschreibung|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE-Fehlercode](../../winscript/reference/script-e-propagate-error-code.md)|Ein Skriptfehler wird an den Aufrufer in einem anderen Thread, die möglicherweise weitergegeben.|  
|[SCRIPT_E_RECORDED-Fehlercode](../../winscript/reference/script-e-recorded-error-code.md)|Ein Fehler wurde zwischen der Skript-Engine und dem Host übergeben.|  
|[SCRIPT_E_REPORTED-Fehlercode](../../winscript/reference/script-e-reported-error-code.md)|Die Skript-Engine hat eine nicht behandelte Ausnahme an den Host gemeldet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)