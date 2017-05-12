---
title: "IScriptNode::CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode::CreateChildEntry
Fügt eine untergeordnete Instanz von `IScriptEntry` hinzu.  
  
## Syntax  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parameter  
 `isn`  
 \[in\] Der Index des untergeordneten Elements im übergeordneten.  
  
 `dwCookie`  
 \[in\] Ein Anwendung festgelegten Wert verwendet, um den untergeordneten Eintrag mit dem Hostobjekt zuzuordnen.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-von\-SkriptBlock Trennzeichens.  Zur Analyse verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen ermöglicht das Skripterstellungsmodul, um Vorverarbeitung bereitzustellen.  Beispielsweise hat das Modul möglicherweise ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen.  Das Modul bestimmt, wie das Trennzeichen verwendet wird.  
  
 Legen Sie den auf NULL, wenn ein Trennzeichen nicht das Ende des Skriptblocks markiert.  
  
 `ppse`  
 \[out\] Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`\-Schnittstelle der untergeordneten Instanz empfängt.  
  
 Für `IScriptNode`\-Objekte, die eine Webseite darstellen, gibt dieses Parameters eine `IScriptEntry`\-Instanz, die einen Skriptblock angibt.  
  
 Für `IScriptEntry`\-Objekte, die einen Skriptblock darstellen, gibt dieses Parameters eine Instanz `IScriptEntry`, die ein Funktionsobjekt angibt.  
  
 Für `IScriptEntry`\-Objekte, die ein Funktionsobjekt darstellen, schlägt diese Methode aus.  
  
 Für `IScriptScriptlet`\-Objekte schlägt diese Methode aus.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `IScriptNode`\-Schnittstelle stellt eine Webseite oder seine Elemente dar.  Die `IScriptEntry`\-Schnittstelle \(die von `IScriptNode` abgeleitet ist\), stellt entweder einen Skriptblock oder ein Funktionsobjekt dar.  Die `IScriptScriptlet`\-Schnittstelle \(die von `IScriptEntry` abgeleitet ist\), wird ein Ereignishandler dar.  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)