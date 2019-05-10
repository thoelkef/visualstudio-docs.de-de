---
title: Launch | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c910ef1519181f1402cbec1d31686492e30f343d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104303"
---
# <a name="launch"></a>Starten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Option **Launch** startet den Profiler mit der Beispielmethode sowie die angegebene Anwendung.  
  
 Um **Launch** zu verwenden, müssen Sie die Methode **Sample** in der Option **Start** angeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `AppName`  
 Der Name der zu startenden Anwendung. Es werden sowohl vollständige als auch partielle Pfade aus dem aktuellen Verzeichnis unterstützt.  
  
## <a name="valid-options"></a>Gültige Optionen  
 Die folgenden VSPerfCmd-Optionen können mit der Option **Launch** in derselben Befehlszeile kombiniert werden.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen-Profilersitzung und legt die angegebene Profilerstellungsmethode fest  
  
 **GlobalOn** und **GlobalOff**  
 Setzt die Profilerstellung fort (**GlobalOn**) oder unterbricht sie (**GlobalOff**), aber nicht die Profilerstellungssitzung  
  
 **ProcessOn:** `PID` und **ProcessOff**:`PID`  
 Setzt die Profilerstellung für den angegebenen Prozess fort (**ProcessOn**) oder unterbricht sie (**ProcessOff**)  
  
 **TargetCLR**  
 Gibt die Version der .NET Framework-CLR (Common Language Runtime) für die Profilerstellung an, wenn mehr als eine Version in einer Profilerstellungssitzung geladen wird. Standardmäßig wird für die zuerst geladene Version ein Profil erstellt.  
  
## <a name="exclusive-options"></a>Ausschließliche Optionen  
 Die folgende Option kann nur mit der Option **Launch** (Start) verwendet werden.  
  
 **Konsole**  
 Startet die angegebene Befehlszeilen-Anwendung in einem neuen Fenster  
  
 **Args:** `ArgList`  
 Gibt eine Liste von Argumenten an, die an die Anwendung übergeben werden sollen  
  
 **LineOff**  
 Deaktiviert das Erfassen von Profilerstellungsdaten auf Zeilenebene.  
  
## <a name="sampling-options"></a>Samplingoptionen  
 Eine der folgenden Optionen für Samplingintervalle kann in der **Launch**-Befehlszeile angegeben werden. Das Standardsamplingintervall sind 10.000.000 Prozessortaktzyklen.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**|**lifetime**]  
 Gibt die Anzahl und den Typ des Samplingintervalls an  
  
- **Timer**: Sampelt alle nicht angehaltenen `Cycles`-Prozessortaktzyklen. Wenn `Cycles` nicht angegeben ist, wird ein Intervall von 10.000.000 festgelegt.  
  
- **PF**: Sampelt alle `Events`-Seitenfehler. Wenn `Events` nicht angegeben ist, geschieht dies bei jedem 10. Seitenfehler.  
  
- **Sys**: Sampelt `Events`-Aufrufe des Betriebssystems. Wenn `Events` nicht angegeben ist, wird jeder 10. Systemaufruf untersucht.  
  
- **Counter**: Sampelt alle `Reload`-Zahlen der von `Name` angegebenen CPU-Leistungsindikatoren. `FriendlyName` kann optional eine Zeichenfolge angeben, die als Spaltenüberschrift in Profilerberichten verwendet wird.  
  
- **GC**: Sammelt .NET-Speicherdaten. Wenn der Parameter **Allocation** angegeben wird (Standard), werden Daten bei jedem Speicherbelegungsereignis gesammelt. Wenn jedoch der **Lifetime**-Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection-Ereignis gesammelt.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Verwenden von **Launch** zum Starten einer Anwendung veranschaulicht.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
