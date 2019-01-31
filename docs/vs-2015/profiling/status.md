---
title: Status | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f64364caf914c030fef806c5ae17e90a8368fa3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770958"
---
# <a name="status"></a>Status
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPerfCmd.exe-Option **Status** zeigt Informationen über den Status des Profilers und aller Prozesse, für die gerade ein Profil erstellt wird.  
  
 Die Option **Status** darf als einzige Option in der Befehlszeile angegeben werden. Der Profiler muss mit der VSPerfCmd.exe-Option **Start** initialisiert werden, bevor ein Status angezeigt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parameter  
 Keiner  
  
## <a name="remarks"></a>Hinweise  
 Die Option **Status** zeigt die folgenden Statusinformationen für den Profiler an.  
  
 **Name der Ausgabedatei**  
 Der Pfad und der Name der aktuellen Profiler-Datendatei  
  
 **Sammlungsmodus**  
 SAMPLE oder TRACE  
  
 **Maximale Anzahl von Prozessen**  
 Die maximale Anzahl von Prozessen, für die gleichzeitig ein Profil erstellt werden kann und die maximale Anzahl der derzeit aktiven Prozesse  
  
 **Maximale Anzahl von Threads**  
 Die maximale Anzahl von Threads, für die gleichzeitig ein Profil erstellt werden kann  
  
 **Anzahl der Puffer**  
 Die Anzahl der Speicherpuffer, die Profilerstellungsdaten schreiben  
  
 **Puffergröße**  
 Die Größe eines Speicherpuffers in Bytes  
  
 Die Option **Status** zeigt die folgenden Statusinformationen für jeden Prozess an, für den gerade ein Profil erstellt wird.  
  
 **Process**  
 Der Name des Prozesses, für den ein Profil erstellt wurde  
  
 **Prozess-ID**  
 Der Systembezeichner des Prozesses  
  
 **Anzahl der Threads**  
 Die Anzahl der Threads, die momentan ausgeführt werden  
  
 **Start/Stop-Zähler**  
 Der primäre Profilerzähler zum Steuern der Datensammlung für diesen Prozess. Der Zähler muss eins sein, damit Daten gesammelt werden. Die Start/Stop-Zähler kann von den Profiler-APIs und den VSPerfCmd-Optionen **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** und **ThreadOff** bearbeitet werden.  
  
 **Suspend/Resume-Zähler**  
 Der sekundäre interne Profilerzähler zum Steuern der Datensammlung für diesen Prozess. Sie muss kleiner als oder gleich 0 (null) sein, um Daten zu sammeln. Der **Suspend/Resume-Zähler** kann nur von den Profiler-APIs bearbeitet werden.  
  
 **Benutzer mit Zugriffsrechten für die Überwachung**  
 Listet die Namen der Benutzer mit Zugriff auf den Profiler auf. Zusätzlichen Benutzern kann mithilfe der VSPerfCmd.exe-Option **Admin** Zugriff gewährt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
