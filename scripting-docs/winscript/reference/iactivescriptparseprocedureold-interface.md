---
title: "IActiveScriptParseProcedureOld-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld-Schnittstelle"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld-Schnittstelle
Hier können die Quellcodetext die zu dem Skript hinzugefügt werden, Prozeduren.  Für interpretierte Skriptsprachen, die keine unabhängige Erstellungsumgebung, wie VBScript haben, stellt dies ein alternativer Mechanismus \(außer `IActiveScriptParse` oder `IPersist*`\) um Skriptprozeduren dem Namespace hinzuzufügen.  
  
> [!NOTE]
>  Diese Schnittstelle wird zugunsten der `IActiveScriptParseProcedure`\-Schnittstelle veraltet.  
  
## Methoden  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IActiveScriptParseProcedureOld`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analysiert die angegebene Kennzahlprozedur und fügt die Prozedur dem Namespace hinzu.|  
  
## Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)