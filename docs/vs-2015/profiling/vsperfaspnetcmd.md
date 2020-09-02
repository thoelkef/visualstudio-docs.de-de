---
title: VSPerfASPNetCmd | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9cb81f17abd1e7891dc3f78a85d6d1276991f070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145275"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Befehlszeilentool **VSPerfASPNetCmd.exe** können Sie ASP.NET-Websites profilen, ohne dass Sie Umgebungsvariablen festlegen und ohne dass Sie Ihren Computer neu starten müssen. Verwenden Sie statt [VSPerfCmd](../profiling/vsperfcmd.md)**VSPerfASPNetCmd.exe**, wenn Sie eine ASP.NET-Website profilen. Dann benötigen Sie nicht die zusätzlichen Funktionen, die **VSPerCmd** bereitstellt. Weitere Informationen zu **VSPerfASPNETCmd** finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** ist das bevorzugte Befehlszeilentool, wenn mit dem eigenständigen Profiler ein Profil für ASP.NET-Websites erstellt wird.  
  
## <a name="syntax"></a>Syntax  
 **vsperfaspnetcmd** [/*Optionen*] *Website*  
  
## <a name="options"></a>Optionen  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**/Sample** oder **/s**|Erstellt Profile für Websites mit der Samplingmethode. **/Sample** ist die Standardmethode. /Sample kann nicht mit **/Trace** verwendet werden.|  
|**/Trace** oder **/t**|Erstellt Profile für Websites mit der Instrumentationsmethode. /Trace kann nicht mit **/Sample** verwendet werden.|  
|**/Memory**[ **:** `Type`] oder **/m**[ **:** {**a**&#124;**l**}]|Erstellt ein Profil für die Arbeitsspeicherzuweisung und erstellt optional Profile für Objektlebensdauern (automatische Speicherbereinigung). **/Memory** kann weder mit der Sampling- noch mit der Instrumentationsmethode verwendet werden.<br /><br /> Als *Type* kann eines der folgenden Elemente verwendet werden:<br /><br /> -   **allocation** (oder **a**) erfasst nur Daten zur Arbeitsspeicherzuweisung<br />-   **lifetime** (oder **l**) erfasst Daten zur Speicherbelegung und zur Objektlebensdauer.<br /><br /> Der Standard-`Type` ist **allocation**.|  
|**/Tip** oder **/i**|Fügt eine ausführliche ASP.NET-Anforderung und einen ADO.NET-Aufrufinformationen zu den Profilerstellungsdaten hinzu **/Tip** kann mit der Sampling- oder der Instrumentationsmethode verwendet werden und mit der Option **/Memory**.|  
|**/Output:** `File` oder **/o:** `File`|Gibt den Namen und den Speicherort der Profilerstellungs-Datendatei (VSP-Datei) an|  
|**/NoWait** oder **/n**|Gibt die Eingabeaufforderung sofort wieder zurück, damit zusätzliche Befehle im Eingabeaufforderungsfenster verwendet werden können. Sie müssen **VSPerfASPNETCmd /Shutdown** in eine Befehlszeile eingeben, um die Profilerstellung zu deaktivieren|  
|**/PackSymbols**[:{**on**&#124;**off**} oder **/p**[:{**on**&#124;**off**}|Bettet Symbole (z.B. Funktions- und Parameternamen) in Profilerstellungsdatendateien ein (VSP-Dateien).|  
|**/Shutdown:** `Website` oder **/d:** `Website`|Deaktiviert die Profilerstellung Verwenden Sie diese Option in einer Befehlszeile nachdem Sie die Option **/NoWait** verwendet haben, um die Profilerstellung zu starten, oder wenn der Profiler unerwartet beendet wurde. Geben Sie die gleiche URL an, die Sie im ursprünglichen **VSPerfASPNETCmd**-Befehl verwendet haben.|  
|`Website`|Die URL der Website, für die ein Profil erstellt werden soll|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnelle Website-Profilerstellung mit vsperfaspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
