---
title: SCRIPTSTATE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff935e54e42eef6691948a7e0d91a495c5153adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097798"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE-Enumeration
Gibt den Zustand einer Skript-Engine. Diese Enumeration wird verwendet, durch die [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) , und [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methoden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
|SCRIPTSTATE_UNINITIALIZED|Skript wurde erst kürzlich erstellt wurde, aber es wurde noch nicht initialisiert wurde mit einer `IPersist*` Schnittstelle und [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skript ist initialisiert wurde, jedoch nicht ausgeführt wird (Herstellen einer Verbindung mit anderen Objekten oder Auffangen von Ereignissen) oder Ausführen von Code. Code für die Ausführung abgefragt werden kann, durch den Aufruf der [IActiveScriptParse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) Methode.|  
|SCRIPTSTATE_STARTED|Skriptausführung kann Code, aber noch nicht die Ereignisse von Objekten, die hinzugefügt werden, indem Sie Auffangen wird die [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) Methode.|  
|SCRIPTSTATE_CONNECTED|Skript wird geladen und für senkereignisse verbunden sind.|  
|SCRIPTSTATE_DISCONNECTED|Skript wird geladen und verfügt über einen Zustand der laufzeitausführung, aber vorübergehend von Auffangen von Ereignissen getrennt wird.|  
|SCRIPTSTATE_CLOSED|Skript wurde geschlossen. Die Skript-Engine funktioniert nicht mehr und gibt für die meisten Methoden Fehler zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)