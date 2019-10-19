---
title: Active Script-Konstanten, Enumerationen und Fehler Codes | Microsoft-Dokumentation
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
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572710"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Konstanten, Enumerationen und Fehlercodes für Active Script
In diesem Abschnitt werden die in Windows Scripting Engines verwendeten Enumerationen und Fehlercodes beschrieben.  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTTHREADID-Konstanten](../../winscript/reference/scriptthreadid-constants.md)|Gibt den Typ des Threads an.|  
  
## <a name="properties"></a>Eigenschaften  
  
|property|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Wird verwendet, um anzugeben, ob die Skript-Engine voll funktionsfähig bleibt, wenn ausstehende Verweise vorhanden sind.|  
  
## <a name="enumerations"></a>Enumerationen  
  
|Enumeration|Beschreibung|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE-Enumeration](../../winscript/reference/scriptgctype-enumeration.md)|Der Typ der auszuführenden Garbage Collection.|  
|[SCRIPTLANGUAGEVERSION-Enumeration](../../winscript/reference/scriptlanguageversion-enumeration.md)|Gibt die möglichen Skript Versionen an.|  
|[SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md)|Gibt den Status einer Skript-Engine an.|  
|||  
|[SCRIPTTHREADSTATE-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md)|Gibt den Status eines Threads in einer Skript-Engine an.|  
|[SCRIPTTRACEINFO-Enumeration](../../winscript/reference/scripttraceinfo-enumeration.md)|Stellt das Skript Ereignis dar, das nachverfolgt wird. Wird in der [iactivescriptsitetraceingefo:: sendscripttracinput Info-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)verwendet.|  
|[SCRIPTUICHANDLING-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md)|Stellt die Methode dar, mit der das UI-Steuerelement behandelt werden soll.|  
|[SCRIPTUICITEM-Enumeration](../../winscript/reference/scriptuicitem-enumeration.md)|Stellt den Typ des Benutzeroberflächen Elements dar. Wird in der [iactivescriptsiteuicontrol:: getuibehavior-Methode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)verwendet.|  
  
## <a name="error-codes"></a>Fehlercodes  
  
|Fehlercode|Beschreibung|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE-Fehlercode](../../winscript/reference/script-e-propagate-error-code.md)|Ein Skript Fehler wird an den Aufrufer weitergegeben, der sich möglicherweise in einem anderen Thread befindet.|  
|[SCRIPT_E_RECORDED-Fehlercode](../../winscript/reference/script-e-recorded-error-code.md)|Zwischen der Skript-Engine und dem Host wurde ein Fehler ausgegeben.|  
|[SCRIPT_E_REPORTED-Fehlercode](../../winscript/reference/script-e-reported-error-code.md)|Die Skript-Engine hat eine nicht behandelte Ausnahme an den Host gemeldet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)