---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
Gibt Sprachinformationen zurück.  
  
## Syntax  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### Parameter  
 `pgrfasa`  
 \[out\] Die Flags, die Sprachinformationen enthalten.  Kann eine Kombination der folgenden Werte:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Die Sprache bevorzugt Skriptereignishandlererstellung durch das Skripterstellungsmodul anstelle der Anwendung.|  
|fasaSupportInternalHandler|0x0002|Die Unterstützung sowie die Ereignishandler, die durch das Skripterstellungsmodul erstellt werden.|  
|fasaCaseSensitive|0x0004|Die Skriptsprache wird die Groß\-\/Kleinschreibung beachtet.|  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Wenn das Skripterstellungsmodul Ereignishandler verwaltet, sollte die Anwendung `CreateChildHandler` von einem `IScriptEntry`\-Objekt aufrufen.  Dies `IScriptScriptlet` erstellt ein Objekt, das dem Ereignishandler entspricht.  Das Modul wird auch ein Ereignishandler dem Skripteintrag hinzu.  Der Ereignishandler wird eine leere Funktion, die die Signaturinformationen enthält.  
  
 Wenn die Anwendung Ereignishandler verwaltet, sollte sie `CreateChildHandler` von einem `IScriptNode`\-Objekt aufrufen, das ein Ereignishandlerskriptlet darstellt.  Es wird ein `IScriptScriptlet`\-Objekt, das mit dem Ereignishandlerskriptlet zugeordnet ist.  Die Anwendung muss eine leere Funktion als Ereignishandler einem neuen oder vorhandenen `IScriptEntry`\-Objekt hinzufügen.  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)