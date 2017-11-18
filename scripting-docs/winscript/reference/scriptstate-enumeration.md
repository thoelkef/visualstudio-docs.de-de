---
title: SCRIPTSTATE-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE-Enumeration
Gibt den Status des ein Skriptmodul. Diese Enumeration wird verwendet, durch die [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , und [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methoden.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Skript erst kürzlich erstellt wurde, aber es wurde noch nicht initialisiert wurde mit einer `IPersist*` Schnittstelle und [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skript ist wurde initialisiert, jedoch nicht ausgeführt (Herstellen einer Verbindung mit anderen Objekten oder Auffangen von Ereignissen) oder Ausführen eines beliebigen Codes. Code für die Ausführung abgefragt werden kann, durch Aufrufen der [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) Methode.|  
|SCRIPTSTATE_STARTED|Skripts kann Code ausgeführt werden, aber nicht noch die Ereignisse von hinzugefügten Objekte Auffangen von ist das [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) Methode.|  
|SCRIPTSTATE_CONNECTED|Skript geladen und für Auffangen von Ereignissen verbunden sind.|  
|SCRIPTSTATE_DISCONNECTED|Skript wird geladen und dem Status zur laufzeitausführung, aber von Auffangen von Ereignissen vorübergehend getrennt wird.|  
|SCRIPTSTATE_CLOSED|Skript wurde geschlossen. Das Skriptmodul funktioniert nicht mehr und gibt für die meisten Methoden Fehler zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)