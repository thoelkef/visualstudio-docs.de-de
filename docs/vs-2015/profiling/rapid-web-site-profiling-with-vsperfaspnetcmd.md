---
title: Schnelle Website-Profilerstellung mit VSPerfASPNETCmd | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e213f6c009ff5fdd5caa48a326c18026f02ec5e6
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590686"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Schnelle Website-Profilerstellung mit VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [schnelle Website-Profilerstellung mit VSPerfASPNETCmd](https://docs.microsoft.com/visualstudio/profiling/rapid-web-site-profiling-with-vsperfaspnetcmd).  
  
Mit dem Befehlszeilentool **VSPerfASPNETCmd** können Sie problemlos Profile für [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen erstellen. Verglichen mit dem [VSPerfCmd](../profiling/vsperfcmd.md)-Befehlszeilentool stehen weniger Optionen zur Verfügung, müssen keine Umgebungsvariablen festgelegt werden und ein Neustart des Computers ist nicht erforderlich. Die Verwendung von **VSPerfASPNETCmd** ist die bevorzugte Methode für die Profilerstellung mit dem eigenständigen Profiler. Weitere Informationen finden Sie unter [How to: Install the Stand-Alone Profiler (Vorgehensweise: Installieren des eigenständigen Profiler)](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In einigen Szenarios, z.B. beim Sammeln von Parallelitätsdaten oder Anhalten und Fortsetzen von Profilerstellungen, ist **VSPerfCmd** die bevorzugte Profilerstellungsmethode.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Verwenden Sie das VSPerfASPNETCmd-Tool im 32-Bit-Verzeichnis \Team Tools\Performance Tools auf 64-Bit-Computern. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Specifying the Path to Command Line Tools (Angeben des Pfads für Befehlszeilentools)](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilerstellung einer ASP.NET-Anwendung  
 Geben Sie einen der in den folgenden Abschnitten beschriebenen Befehle ein, um ein Profil für eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung zu erstellen. Die Website wird gestartet, und die Datensammlung durch den Profiler beginnt. Verwenden Sie die Anwendung, und schließen Sie den Browser. Drücken Sie die Eingabetaste im Eingabeaufforderungsfenster, um die Profilerstellung zu beenden.  
  
> [!NOTE]
>  In der Standardeinstellung wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**-Befehl nicht zurückgeben. Sie können die Option **/nowait** nutzen, um die Rückgabe der Befehlsaufforderung zu erzwingen. Siehe [Using the /NoWait option (Verwenden der /NoWait-Option)](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Zum Sammeln von Anwendungsstatistiken mithilfe der Samplingmethode  
 Das Sampling ist die standardmäßige Profilerstellungsmethode des Tools **VSPerfASPNETCmd** und muss nicht in der Befehlszeile angegeben werden. Die folgende Befehlszeile sammelt Anwendungsstatistiken über die angegebene Webanwendung:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Sammeln von ausführlichen Zeitsteuerungsdaten mit der Instrumentierungsmethode  
 Verwenden Sie die folgende Befehlszeile zum Sammeln ausführlicher Zeitsteuerungsdaten aus einer dynamisch kompilierten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung:  
  
 **vsperfaspnetcmd /trace**  *websiteUrl*  
  
 Wenn Sie für statisch kompilierte DLL-Dateien in Ihrer Webanwendung ein Profil erstellen möchten, müssen Sie die Dateien mithilfe des Befehlszeilentools [VSInstr](../profiling/vsinstr.md) instrumentieren. Der Vsperfaspnetcmd/Trace-Befehl wird Daten aus den instrumentierten Dateien enthalten.  
  
## <a name="to-collect-net-memory-data"></a>Sammeln von .NET-Speicherdaten  
 Die **/Memory**-Option sammelt Daten zur Zuordnung von Objekten im .NET- Speicher und kann Daten über die Lebensdauer dieser Objekte sammeln. Sammeln von Speicherbelegungsdaten ist der Standardmodus der **/Memory**-Datenoption und muss nicht in der Befehlszeile angegeben werden.  
  
 **vsperfaspnetcmd /memory** *websiteUrl*  
  
 Verwenden der **Lebensdauer**-Parameter zum Sammeln von Objektlebensdauerdaten zusätzlich zu den Speicherbelegungsdaten:  
  
 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*  
  
 Sie können auch die **/Trace**-Option verwenden, um ausführliche Zeitsteuerungsinformationen in die .NET-Speicherdaten einzuschließen:  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Erfassen von Ebeneninteraktionsdaten  
  
> [!WARNING]
>  Profilerstellungsdaten für die Ebeneninteraktion (TIP) können mit [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] und [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]angezeigt werden.  
>   
>  Sie müssen zum Erfassen von TIP-Daten auf Windows 8 oder Windows Server 2012 die Instrumentationsoption (**/trace**) verwenden.  
  
 Erfassen von Ebeneninteraktionsdaten mit Samplingdaten:  
  
 **vsperfaspnetcmd /tip** `websiteUrl`  
  
 Sammeln von Ebeneninteraktionsdaten mit Instrumentationsdaten:  
  
 **vsperfaspnetcmd /trace /tip** *websiteUrl*  
  
 Sammeln von Ebeneninteraktionsdaten mit .NET-Speicherdaten:  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_  
  
##  <a name="UsingNoWait"></a> Verwenden der /NoWait-Option  
 In der Standardeinstellung wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**-Befehl nicht zurückgeben. Sie können die folgende Syntaxoption verwenden, um die Rückgabe des Befehls zu erzwingen. Sie können dann andere Vorgänge im Eingabeaufforderungsfenster ausführen. Verwenden Sie zum Beenden der Profilerstellung die **/shutdown**-Option in einem separaten **vsperfaspnetcmd**-Befehl.  
  
 So beginnen Sie mit der Profilerstellung:  
  
 **vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_  
  
 So beenden Sie die Profilerstellung:  
  
 **vsperfaspnetcmd /shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Zusätzliche Optionen  
 Sie können eine der folgenden Optionen zu den weiter oben in diesem Abschnitt aufgelisteten Befehlen hinzufügen, mit Ausnahme des Befehls **vsperfaspnetcmd/shutdown**.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**/Output:** `VspFile`|Standardmäßig wird die Profilerstellungsdatendatei (.vsp) im aktuellen Verzeichnis mit dem Dateinamen **PerformanceReport.vsp** erstellt. Verwenden Sie die Option /Output, um einen anderen Speicherort, Dateinamen oder beides anzugeben.|  
|**/PackSymbols:Off**|Standardmäßig bettet VsPerfASPNETCmd Symbole (Funktion und Parameternamen usw.) in die VSP-Datei ein. Das Einbetten der Symbole kann die Profilerstellungsdatendatei sehr groß werden lassen. Wenn Sie auf die PDB-Dateien zugreifen können, die die Symbole enthalten, wenn Sie die Daten analysieren, verwenden Sie die Option /packsymbols: off, um die Einbettung der Symbole zu deaktivieren.|



