---
title: VSPerfASPNetCmd | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: ab57983a9dec6ce00e9edef4027b2a23f47d2ae1
ms.contentlocale: de-de
ms.lasthandoff: 08/10/2017

---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Mit dem Befehlszeilentool **VSPerfASPNetCmd.exe** können Sie ASP.NET-Websites profilen, ohne dass Sie Umgebungsvariablen festlegen und ohne dass Sie Ihren Computer neu starten müssen. Verwenden Sie statt [VSPerfCmd](../profiling/vsperfcmd.md) **VSPerfASPNetCmd.exe**, wenn Sie eine ASP.NET-Website profilen. Dann benötigen Sie nicht die zusätzlichen Funktionen, die **VSPerfCmd** bereitstellt. Weitere Informationen zu **VSPerfASPNETCmd** finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). VSPerfASPNETCmd ist das bevorzugte Tool, wenn mit dem eigenständigen Profiler ein Profil für ASP.NET-Websites erstellt wird.  
  
## <a name="syntax"></a>Syntax  
 **vsperfaspnetcmd** [/*Optionen*] *Website*  
  
## <a name="options"></a>Optionen  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**/Sample** oder **/s**|Erstellt Profile für Websites mit der Samplingmethode. **/Sample** ist die Standardmethode. /Sample kann nicht mit **/Trace** verwendet werden.|  
|**/Trace** oder **/t**|Erstellt Profile für Websites mit der Instrumentationsmethode. /Trace kann nicht mit **/Sample** verwendet werden.|  
|**/Memory**[**:**`Type`] oder **/m**[**:**{**a**&#124;**l**}]|Erstellt ein Profil für die Arbeitsspeicherzuweisung und erstellt optional Profile für Objektlebensdauern (automatische Speicherbereinigung). **/Memory** kann weder mit der Sampling- noch mit der Instrumentationsmethode verwendet werden.<br /><br /> Als *Type* kann eines der folgenden Elemente verwendet werden:<br /><br /> -   **allocation** (oder **a**) erfasst nur Daten zur Arbeitsspeicherzuweisung<br />-   **lifetime** (oder **l**) erfasst Daten zur Speicherbelegung und zur Objektlebensdauer.<br /><br /> Der Standard-`Type` ist **allocation**.|  
|**/Tip** oder **/i**|Fügt eine ausführliche ASP.NET-Anforderung und einen ADO.NET-Aufrufinformationen zu den Profilerstellungsdaten hinzu **/Tip** kann mit der Sampling- oder der Instrumentationsmethode verwendet werden und mit der Option **/Memory**.|  
|**/Output:** `File` oder **/o:**`File`|Gibt den Namen und den Speicherort der Profilerstellungs-Datendatei (VSP-Datei) an|  
|**/NoWait** oder **/n**|Gibt die Eingabeaufforderung sofort wieder zurück, damit zusätzliche Befehle im Eingabeaufforderungsfenster verwendet werden können. Sie müssen **VSPerfASPNETCmd /Shutdown** in eine Befehlszeile eingeben, um die Profilerstellung zu deaktivieren|  
|**/PackSymbols**[:{**on**&#124;**off**} oder **/p**[:{**on**&#124;**off**}|Bettet Symbole (Funktions- und Parameternamen usw.) in Profilerstellungs-Datendateien ein (.vsp)|  
|**/Shutdown:** `Website`oder **/d:**`Website`|Deaktiviert die Profilerstellung Verwenden Sie diese Option in einer Befehlszeile nachdem Sie die Option **/NoWait** verwendet haben, um die Profilerstellung zu starten, oder wenn der Profiler unerwartet beendet wurde. Geben Sie die gleiche URL an, die Sie im ursprünglichen **VSPerfASPNETCmd**-Befehl verwendet haben.|  
|`Website`|Die URL der Website, für die ein Profil erstellt werden soll|  
  
## <a name="see-also"></a>Siehe auch  
 [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)

