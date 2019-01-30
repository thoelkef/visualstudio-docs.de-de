---
title: Start | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b719d907402a1671a66a42b3ff9b0295cee6856e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004538"
---
# <a name="start"></a>Starten
Die **Start**-Option ist eine *VSPerfCmd.exe*-Option, die den Profiler mit der angegebenen Profilerstellungsmethode initialisiert.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Method`  
 Eines der folgenden Schlüsselwörter muss angegeben werden:  
  
-   **TRACE**: Gibt die Instrumentationsmethode an.  
  
-   **SAMPLE**: Gibt die Samplingmethode an.  
  
-   **COVERAGE**: Gibt die Abdeckung des Codes an.  
  
-   **CONCURRENCY**: Gibt die Ressourcenkonfliktmethode an.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **Ausgabe** muss angegeben werden, wenn **Start** auf der Befehlszeilen angegeben wird.  
  
 **Ausgabe:**`filename`  
 Gibt den Ausgabedateinamen an.  
  
## <a name="exclusive-options"></a>Ausschließende Optionen  
 Die folgenden Optionen können nur mit der Option **Start** in einer Befehlszeile verwendet werden.  
  
 **CrossSession**&#124;**CS**  
 Ermöglicht die prozessübergreifende Profilerstellung. Die Optionsnamen **CrossSession** und **CS** werden beide unterstützt.  
  
 **User:**[`domain\`]`username`  
 Ermöglicht dem Client Zugriff auf den Monitor vom angegebenen Konto aus.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** gibt einen Windows-Leistungsindikator an, der als Markierung in die Profilerstellungsdatendatei aufgenommen werden soll. **AutoMark** gibt das Intervall in Millisekunden zwischen dem Erfassen der Datendatei an.  
  
## <a name="invalid-options"></a>Ungültige Optionen  
 Die folgenden Optionen können nicht mit der Option **Start** in einer Befehlszeile verwendet werden.  
  
 **Status**  
 **Status** gilt für die Prozesse, von denen ein Profil erstellt wurde. Prozesse und Threads und der aktuelle Zustand der Profile (ein/aus) wird hier aufgeführt. Wenn beispielsweise ein Prozess beendet wird, gibt **Status** dies nicht im Bericht an. **Status** zeigt an, ob vom Prozess ein Profil erstellt wird.  
  
 **Shutdown**[**:**`Timeout`]  
 Deaktiviert den Profiler.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht, wie die Option **Start** von *VSPerfCmd.exe* den Profiler initialisiert.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)