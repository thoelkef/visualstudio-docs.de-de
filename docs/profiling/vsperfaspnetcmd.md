---
title: "VSPerfASPNetCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Befehlszeilentool **VSPerfASPNetCmd.exe** ermöglicht das Erstellen von Profilen für ASP.NET\-Websites ohne die Erstellung von Umgebungsvariablen oder einen Neustart des Computers.  Verwenden Sie **VSPerfASPNetCmd.exe** anstelle von [VSPerfCmd](../profiling/vsperfcmd.md), wenn Sie Profile für ASP.NET\-Websites erstellen möchten und die zusätzlichen Funktionen von **VSPerCmd** nicht benötigen.  Weitere Informationen zu **VSPerfASPNetCmd** finden Sie unter [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  Bei **VSPerfASPNetCmd** handelt es sich um das bevorzugte Befehlszeilentool, zum Erstellen eines Profils für eine ASP.NET\-Website mithilfe des eigenständigen Profilers.  
  
## Syntax  
 **vsperfaspnetcmd** \[\/*Options*\] *Website*  
  
## Optionen  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**\/Sample** oder   **\/s**|Erstellt ein Profil für die Website unter Verwendung der Samplingmethode.  **\/Sample** ist die Standardmethode. "\/Sample" kann nicht zusammen mit **\/Trace** verwendet werden.|  
|**\/Trace** oder   **\/t**|Erstellt ein Profil für die Website unter Verwendung der Instrumentationsmethode. "\/Trace" kann nicht zusammen mit **\/Sample** verwendet werden.|  
|**\/Memory**\[**:**`Type`\]                  oder   **\/m**\[**:**{**a**&#124;**l**}\]|Erstellt ein Profil für die Speicherbelegung und optional für die Lebensdauer von Objekten \(Garbage Collection\).  **\/Memory** kann mit der Sampling\- oder mit der Instrumentationsmethode verwendet werden.<br /><br /> *Type* kann eines der folgenden Elemente sein:<br /><br /> -   Bei **allocation** \(oder **a**\) werden ausschließlich Speicherbelegungsdaten gesammelt.<br />-   Bei **lifetime** \(oder **l**\) werden Daten zur Speicherbelegung und zur Objektlebensdauer gesammelt.<br /><br /> Der Standardwert für `Type` ist **allocation**.|  
|**\/Tip** oder   **\/i**|Fügt den Profilerstellungsdaten ausführliche ASP.NET\-Anforderungs\- und ADO.NET\-Aufrufinformationen hinzu.  **\/Tip** kann mit der Sampling\- oder der Instrumentationsmethode sowie zusammen mit der Option **\/Memory** verwendet werden.|  
|**\/Output:** `File`  oder   **\/o:**`File`|Gibt Pfad und Dateiname der Profilerstellungs\-Datendatei \(VSP\-Datei\) an.|  
|**\/NoWait** oder   **\/n**|Gibt umgehend die Eingabeaufforderung zurück, damit im Eingabeaufforderungsfenster zusätzliche Befehle verwendet werden können.  **VSPerfASPNETCmd \/Shutdown** muss in einer separaten Befehlszeile eingegeben werden, um die Profilerstellung zu deaktivieren.|  
|**\/PackSymbols**\[:{**on**&#124;**off**}oder   **\/p**\[:{**on**&#124;**off**}|Bettet Symbole \(Funktions\- und Parameternamen usw.\) in die Profilerstellungs\-Datendatei \(VSP\-Datei\) ein.|  
|**\/Shutdown:** `Website`oder   **\/d:**`Website`|Deaktiviert die Profilerstellung.  Verwenden Sie diese Option als einzige Option in einer Befehlszeile, nachdem die Profilerstellung mithilfe der Option **\/NoWait** gestartet oder der Profiler unerwartet beendet wurde.  Geben Sie die gleiche URL an, die auch im ursprünglichen Befehl vom Typ **VSPerfASPNETCmd** verwendet wurde.|  
|`Website`|Die URL der Website, für die ein Profil erstellt werden soll.|  
  
## Siehe auch  
 [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)