---
title: Erhalten von Buildprotokollen mit MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430845"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Erhalten von Buildprotokollen mit MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Indem Sie Schalter mit MSBuild verwenden, können Sie angeben, wie viele Builddaten zu überprüfen sind und ob Sie Builddaten in eine oder mehrere Dateien speichern möchten. Sie können auch eine benutzerdefinierte Protokollierung zum Sammeln von Builddaten angeben. Weitere Informationen zu MSBuild-Befehlszeilenschalter, die in diesem Thema nicht behandelt werden, finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Wenn Sie Projekte mithilfe von Visual Studio-IDE erstellen, können Sie die Probleme diese Builds beheben, indem Sie Buildprotokolle überprüfen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen, speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Festlegen des Detailgrads  
 Wenn Sie ein Projekt mithilfe von MSBuild ohne Angabe einer Detailebene erstellen, werden die folgenden Informationen im Ausgabeprotokoll angezeigt:  
  
- Fehler, Warnungen und Nachrichten, die als äußerst wichtig eingestuft werden.  
  
- Einige Statusereignisse.  
  
- Eine Übersicht des Build.  
  
  Mithilfe des Schalters **/verbosity** (**/v**) können Sie steuern, wie viele Daten im Ausgabeprotokoll angezeigt werden. Verwenden Sie für die Problembehandlung entweder den Ausführlichkeitsgrad `detailed` (`d`) oder `diagnostic` (`diag`), der die meisten Informationen bietet.  
  
  Der Buildprozess ist möglicherweise langsamer, wenn Sie **/verbosity** auf `detailed` festlegen und sogar langsamer, wenn Sie **/verbosity** auf `diagnostic` festlegen.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Speichern des Buildprotokolls in einer Datei  
 Sie können den Schalter **/fileLogger** (**fl**) verwenden, um Builddaten in einer Datei zu speichern. Im folgenden Beispiel werden die Builddaten in einer Datei mit dem Namen `msbuild.log` gespeichert.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Im folgenden Beispiel heißt die Protokolldatei `MyProjectOutput.log` und der Ausführlichkeitsgrad der Protokollausgabe ist auf `diagnostic` festgelegt. Geben Sie diese beiden Einstellungen mithilfe des Schalters **/filelogparameters** (`flp`) an.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Speichern der Protokollausgabe in mehreren Dateien  
 Im folgenden Beispiel wird das gesamte Protokoll in `msbuild1.log`, nur die Fehler in `JustErrors.log` und nur die Warnungen in `JustWarnings.log` gespeichert. Im Beispiel werden Dateinummern für jede der drei Dateien verwendet. Die Dateinummern werden nach den Schaltern **/fl** und **/flp** angegeben (z.B. `/fl1` und `/flp1`).  
  
 Die Schalter **/filelogparameters** (`flp`) für die Dateien 2 und 3 gibt an, wie jede Datei benannt werden und was sie enthalten soll. Es wird kein Name für die Datei 1 angegeben, deshalb wird der Standardname `msbuild1.log` verwendet.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Verwenden einer benutzerdefinierten Protokollierung  
 Sie können eine eigene Protokollierung schreiben, indem Sie einen verwalteten Typ erstellen, der die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert. Sie können eine benutzerdefinierte Protokollierung verwenden, um z.B. Buildfehler per E-Mail zu versenden, sie in einer Datenbank oder einer XML-Datei zu protokollieren. Weitere Informationen finden Sie unter [Buildprotokollierungen](../msbuild/build-loggers.md).  
  
 In der MSBuild-Befehlszeile geben Sie die benutzerdefinierte Protokollierung mithilfe des Schalters **/logger** an. Sie können auch den Schalter **/noconsolelogger** verwenden, um die Standardkonsole zu deaktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Buildprotokollierungen](../msbuild/build-loggers.md)   
 [Protokollierung in einer Multiprozessorumgebung](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Erstellen von Weiterleitungsprotokollierungen](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
