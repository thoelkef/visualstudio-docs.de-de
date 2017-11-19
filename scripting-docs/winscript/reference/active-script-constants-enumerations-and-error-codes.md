---
title: Active Script-Konstanten, Enumerationen und Fehlercodes | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Konstanten, Enumerationen und Fehlercodes für Active Script
In diesem Abschnitt wird beschrieben, die Enumerationen und Fehlercodes, die in Windows-Skriptmodulen verwendet.  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTTHREADID-Konstanten](../../winscript/reference/scriptthreadid-constants.md)|Gibt den Typ des Threads.|  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Dient zum angeben, und zwar unabhängig davon, ob das Skriptmodul bleiben sollten voll funktionsfähig, wenn ausstehende Verweise vorhanden sind.|  
  
## <a name="enumerations"></a>Enumerationen  
  
|Enumeration|Beschreibung|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE-Enumeration](../../winscript/reference/scriptgctype-enumeration.md)|Der Typ der Garbagecollection auszuführen.|  
|[SCRIPTLANGUAGEVERSION-Enumeration](../../winscript/reference/scriptlanguageversion-enumeration.md)|Gibt die möglichen Versionen scripting an.|  
|[SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md)|Gibt den Status des ein Skriptmodul.|  
|||  
|[SCRIPTTHREADSTATE-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md)|Gibt den Zustand eines Threads in einem Skriptmodul.|  
|[SCRIPTTRACEINFO-Enumeration](../../winscript/reference/scripttraceinfo-enumeration.md)|Stellt das Skriptereignis, das Ablauf verfolgt wird. Verwendet die [iactivescriptsitetraceinfo:: Sendscripttraceinfo-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md)|Stellt die Möglichkeit, dass das UI-Steuerelement behandelt werden soll.|  
|[SCRIPTUICITEM-Enumeration](../../winscript/reference/scriptuicitem-enumeration.md)|Stellt den Typ des Benutzeroberflächenautomatisierungs-Elements dar. Verwendet die [iactivescriptsiteuicontrol:: Getuibehavior-Methode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Fehlercodes  
  
|Fehlercode|Beschreibung|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE-Fehlercode](../../winscript/reference/script-e-propagate-error-code.md)|Ein Skriptfehler wird an den Aufrufer weitergegeben, die in einem anderen Thread möglicherweise.|  
|[SCRIPT_E_RECORDED-Fehlercode](../../winscript/reference/script-e-recorded-error-code.md)|Ein Fehler wurde zwischen dem Skriptmodul und dem Host übergeben.|  
|[SCRIPT_E_REPORTED-Fehlercode](../../winscript/reference/script-e-reported-error-code.md)|Das Skriptmodul hat eine nicht behandelte Ausnahme an den Host gemeldet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)