---
title: "Variablen f&#252;r die bedingte Kompilierung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Bedingte Kompilierung, Variablen"
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Variablen f&#252;r die bedingte Kompilierung (JavaScript)
Folgende vordefinierte Variablen stehen für die bedingte Kompilierung zur Verfügung.  Wenn eine Variable nicht **true** ist, wird sie nicht definiert und verhält sich als `NaN`, wenn auf sie zugegriffen wird.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird in allen Versionen von Internet Explorer vor Internet Explorer 11 unterstützt.  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps nicht unterstützt.  
  
## Variablen  
  
|Variable|Beschreibung|  
|--------------|------------------|  
|@\_win32|True bei Ausführung auf einem Win32\-System.|  
|@\_win16|True bei Ausführung auf einem Win16\-System.|  
|@\_mac|True bei Ausführung auf einem Apple Macintosh\-System.|  
|@\_alpha|True bei Ausführung auf einem DEC Alpha\-Prozessor.|  
|@\_x86|True bei Ausführung auf einem Intel\-Prozessor.|  
|@\_mc680x0|True bei Ausführung auf einem Motorola 680x0\-Prozessor.|  
|@\_PowerPC|True bei Ausführung auf einem Motorola PowerPC\-Prozessor.|  
|@\_jscript|Stets true.|  
|@\_jscript\_build|Enthält die Buildnummer des [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Skriptmoduls.|  
|@\_jscript\_version|Enthält die [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Versionsnummer im Format Hauptversion.Nebenversion.|