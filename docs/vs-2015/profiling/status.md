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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157788"
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
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Die Option **Status** zeigt die folgenden Statusinformationen für den Profiler an.  
  
 **Name der Ausgabedatei**  
 Der Pfad und der Name der aktuellen Profiler-Datendatei  
  
 **Sammlungs Modus**  
 SAMPLE oder TRACE  
  
 **Maximale Anzahl von Prozessen**  
 Die maximale Anzahl von Prozessen, für die gleichzeitig ein Profil erstellt werden kann und die maximale Anzahl der derzeit aktiven Prozesse  
  
 **Maximale Threads**  
 Die maximale Anzahl von Threads, für die gleichzeitig ein Profil erstellt werden kann  
  
 **Anzahl der Puffer**  
 Die Anzahl der Speicherpuffer, die Profilerstellungsdaten schreiben  
  
 **Puffergröße**  
 Die Größe eines Speicherpuffers in Bytes  
  
 Die Option **Status** zeigt die folgenden Statusinformationen für jeden Prozess an, für den gerade ein Profil erstellt wird.  
  
 **Prozess**  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
