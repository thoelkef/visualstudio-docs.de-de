---
title: "SCRIPTSTATE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE-Enumeration"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE-Enumeration
Gibt den Zustand eines Skriptmoduls an.  Diese Enumeration wird durch die [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md), [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) und [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)\-Methoden verwendet.  
  
## Syntax  
  
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
  
## Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|Skript ist nur erstellt wurde, jedoch noch nicht mit einer `IPersist*`\-Schnittstelle und [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) initialisiert.|  
|SCRIPTSTATE\_INITIALIZED|Skript ist initialisiert wurden, aber ausführt \(anschließend an andere Objekte oder sinkende Ereignisse\) oder keinen Code ausführt.  Code kann für Ausführung abgefragt werden, indem die [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)\-Methode aufgerufen wird.|  
|SCRIPTSTATE\_STARTED|Skript kann Code ausführen, jedoch noch nicht sinkt die Ereignisse von den Objekten, die von den [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)\-Methode hinzugefügt werden.|  
|SCRIPTSTATE\_CONNECTED|Skript wird für sinkende Ereignisse geladen und verbunden.|  
|SCRIPTSTATE\_DISCONNECTED|Sie Skripts wird geladen und verfügt über einen Ablaufausführungsstand, jedoch wird vorübergehend getrennt von sinkenden Ereignisse.|  
|SCRIPTSTATE\_CLOSED|Skript ist geschlossen.  Das Skriptmodul nicht mehr funktionieren und gibt Fehler für die meisten Methoden zurück.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)