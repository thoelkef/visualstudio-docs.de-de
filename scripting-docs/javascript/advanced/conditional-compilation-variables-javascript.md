---
title: "Variablen für die bedingte Kompilierung (JavaScript) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-variables-javascript"></a>Variablen für die bedingte Kompilierung (JavaScript)
Folgende vordefinierte Variablen stehen für die bedingte Kompilierung zur Verfügung. Wenn eine Variable nicht **TRUE** ist, wird sie nicht definiert und verhält sich als `NaN`, wenn auf sie zugegriffen wird.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird in allen Versionen von Internet Explorer vor Internet Explorer 11 unterstützt. Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps nicht unterstützt.  
  
## <a name="variables"></a>Variablen  
  
|Variable|Beschreibung|  
|--------------|-----------------|  
|@_win32|True bei Ausführung auf einem Win32-System.|  
|@_win16|True bei Ausführung auf einem Win16-System.|  
|@_mac|True bei Ausführung auf einem Apple Macintosh-System.|  
|@_alpha|True bei Ausführung auf einem DEC Alpha-Prozessor.|  
|@_x86|True bei Ausführung auf einem Intel-Prozessor.|  
|@_mc680x0|True bei Ausführung auf einem Motorola 680x0-Prozessor.|  
|@_PowerPC|True bei Ausführung auf einem Motorola PowerPC-Prozessor.|  
|@_jscript|Stets true.|  
|@_jscript_build|Enthält die Buildnummer des [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skriptmoduls.|  
|@_jscript_version|Enthält die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Versionsnummer im Format Hauptversion.Nebenversion.|