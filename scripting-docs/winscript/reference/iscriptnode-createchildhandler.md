---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
Fügt ein Skriptlet als untergeordnete Instanz von `IScriptNode` hinzu.  
  
## Syntax  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parameter  
 `pszDefaultName`  
 \[in\] Die Adresse des mit dem Skriptlet zuzuordnen, bei.  
  
 `prgpszNames`  
 \[in, size\_is \(`cpszNames`\)\] Eine Liste von Bezeichnern aus dem vollqualifizierten Namen auf dem Host.  
  
 `cpszNames`  
 \[in\] Die Anzahl von Bezeichnern im `prgpszNames`\-Parameter.  
  
 `pszEvent`  
 \[in\] Verknüpft die Pufferadresse, die den Ereignisnamen identifiziert, mit dem Skriptlet zu.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-von\-SkriptBlock Trennzeichens.  Zur Analyse verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptblocks zu erkennen.  
  
 Das Trennzeichen aktiviert Vorverarbeitung durch das Skripterstellungsmodul.  Beispielsweise hat das Modul möglicherweise ein einfaches Anführungszeichen durch zwei einfache Anführungszeichen zur Verwendung als Trennzeichen.  Das Modul bestimmt, wie das Trennzeichen verwendet wird.  
  
 Legen Sie den auf NULL, wenn kein Trennzeichen verwendet wird, um das Ende des Skriptblocks zu identifizieren.  
  
 `ptiSignature`  
 \[in\] Die Typinformationen für ein Funktionsobjekt.  
  
 `iMethodSignature`  
 \[in\] Der Index der Funktion im Parameter `ITypeInfo``ptiSignature`.  
  
 `isn`  
 \[in\] Der Index des untergeordneten Elements im übergeordneten.  
  
 `dwCookie`  
 \[in\] Ein Anwendung festgelegten Wert, der verwendet wird, um den Eintrag mit dem Hostobjekt zuzuordnen.  
  
 `ppse`  
 \[out\] Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`\-Schnittstelle der untergeordneten Instanz empfängt.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Skriptlet gibt einen Ereignishandler auf.  Diese Methode erstellt ein Skriptlet, wenn sie in einem `IScriptNode`\-Objekt aufgerufen wird, das eine Webseite darstellt.  Diese Methode fehl, wenn sie von anderen Schnittstellen aufgerufen wird.  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)