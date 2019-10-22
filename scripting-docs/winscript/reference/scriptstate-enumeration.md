---
title: ScriptState-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575681"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE-Enumeration
Gibt den Status einer Skript-Engine an. Diese Enumeration wird von der [IActiveScript:: getscriptstate](../../winscript/reference/iactivescript-getscriptstate.md) -, [IActiveScript:: setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) -Methode und der [iactivescriptsite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) -Methode verwendet.  
  
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
|SCRIPTSTATE_UNINITIALIZED|Das Skript wurde soeben erstellt, aber noch nicht mit einer `IPersist*`-Schnittstelle und [IActiveScript:: setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) initialisiert.|  
|SCRIPTSTATE_INITIALIZED|Das Skript wurde initialisiert, wird jedoch nicht ausgeführt (Verbindung mit anderen Objekten oder Sink-Ereignissen) oder Ausführen von Code. Der Code kann durch Aufrufen der [iactivescriptparamese::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) -Methode zur Ausführung abgefragt werden.|  
|SCRIPTSTATE_STARTED|Skripts können Code ausführen, aber die Ereignisse von Objekten, die durch die [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) -Methode hinzugefügt wurden, noch nicht unter senken.|  
|SCRIPTSTATE_CONNECTED|Das Skript wird geladen und für Sink-Ereignisse verbunden.|  
|SCRIPTSTATE_DISCONNECTED|Das Skript wird geladen und weist einen Lauf Zeit Ausführungs Status auf, wird aber vorübergehend von den Sink-Ereignissen getrennt.|  
|SCRIPTSTATE_CLOSED|Das Skript wurde geschlossen. Die Skript-Engine funktioniert nicht mehr und gibt für die meisten Methoden Fehler zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)