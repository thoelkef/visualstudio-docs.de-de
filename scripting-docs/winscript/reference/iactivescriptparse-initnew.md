---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
Initialisiert das Skriptmodul.  
  
## Syntax  
  
```  
HRESULT InitNew(void);  
```  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn ein Fehler bei der Initialisierung aufgetreten ist.  
  
## Hinweise  
 Bevor das Skriptmodul verwendet werden kann, muss eine der folgenden Methoden aufgerufen werden: `IPersist*::Load`, `IPersist*::InitNew` oder `IActiveScriptParse::InitNew`.  Die Semantik dieser Methode ist die `IPersistStreamInit::InitNew` identisch, insofern, dass diese Methode das Skriptmodul anweist, sich zu initialisieren.  Beachten Sie, dass sie ungültig ist, `IPersist*::InitNew` oder `IActiveScriptParse::InitNew` und `IPersist*::Load` aufzurufen, noch ist es gültig, `IPersist*::InitNew`, `IActiveScriptParse::InitNew` oder `IPersist*::Load` mehrmals aufzurufen.  
  
## Siehe auch  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)