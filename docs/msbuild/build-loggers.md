---
title: Buildprotokollierungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: ee5db285c55dc3969bd21fe722d7e4bacdcb6f3c
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="build-loggers"></a>Buildprotokollierungen
Protokollierungen bieten eine Möglichkeit, die Ausgabe des Builds anzupassen und Meldungen, Fehler oder Warnungen als Reaktion auf bestimmte Buildereignisse anzuzeigen. Jede Protokollierung wird als .NET- Klasse implementiert, die die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert, die in der Assembly „Microsoft.Build.Framework.dll“ definiert ist.  
  
 Es gibt zwei Ansätze, die Sie verwenden können, wenn Sie eine Protokollierung implementieren:  
  
-   Implementieren Sie die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle direkt.  
  
-   Leiten Sie Ihre Klasse von der Hilfsklasse <xref:Microsoft.Build.Utilities.Logger> ab, die in der Assembly „Microsoft.Build.Utilities.dll“ definiert ist. <xref:Microsoft.Build.Utilities.Logger> implementiert <xref:Microsoft.Build.Framework.ILogger> und bietet standardmäßig Implementierungen einiger <xref:Microsoft.Build.Framework.ILogger>-Elemente.  
  
 In diesem Thema wird erläutert, wie Sie eine einfache Protokollierung schreiben, die von <xref:Microsoft.Build.Utilities.Logger> abgeleitet ist und Meldungen in der Konsole als Reaktion auf bestimmte Buildereignisse anzeigt.  
  
## <a name="registering-for-events"></a>Registrieren für Ereignisse  
 Der Zweck einer Protokollierung ist das Sammeln von Informationen über den Fortschritt des Builds gemäß Meldung durch das Buildmodul und Berichten dieser Informationen auf nützliche Weise. Alle Protokollierungen müssen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>-Methode überschreiben, wo sich die Protokollierung für Ereignisse registriert. In diesem Beispiel registriert sich die Protokollierung für die <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>-, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>Reagieren auf Ereignisse  
 Weil die Protokollierung nun für bestimmte Ereignisse registriert ist, muss sie diese Ereignisse bei ihrem Auftreten behandeln. Für die <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse schreibt die Protokollierung einfach einen kurzen Ausdruck und den Namen der am Ereignis beteiligten Projektdatei. Alle Meldungen aus der Protokollierung werden im Konsolenfenster ausgegeben.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Reagieren auf Ausführlichkeitswerte der Protokollierung  
 In einigen Fällen möchten Sie möglicherweise nur Informationen von einem Ereignis protokollieren, wenn der Schalter **/verbosity** von „MSBuild.exe“ einen bestimmten Wert enthält. In diesem Beispiel protokolliert der <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>-Ereignishandler nur dann eine Meldung, wenn die <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>-Eigenschaft, die durch den Schalter **/verbosity** festgelegt wird, gleich <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed` ist.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>Festlegen einer Protokollierung  
 Nachdem die Protokollierung in eine Assembly kompiliert worden ist, müssen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mitteilen, diese Protokollierung während der Builderstellung zu verwenden. Dies erfolgt mithilfe des Schalters **/logger** von „MSBuild.exe“. Weitere Informationen zu den verfügbaren Schaltern für „MSBuild.exe“ finden Sie in der [MSBuild Command-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
 Die folgende Befehlszeile erstellt das Projekt `MyProject.csproj` und verwendet die in `SimpleLogger.dll` implementierte Protokollierungsklasse. Der Schalter **/nologo** blendet Banner und Copyrightmeldung aus, und **/noconsolelogger** deaktiviert die standardmäßige [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Konsolenprotokollierung.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Die folgende Befehlszeile erstellt das Projekt mit der gleichen Protokollierung, jedoch mit dem `Verbosity`-Grad `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel enthält den vollständigen Code für die Protokollierung.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>Kommentare  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt das Implementieren einer Protokollierung, die das Protokoll in eine Datei schreibt, anstatt es im Konsolenfenster anzuzeigen.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>Kommentare  
  
## <a name="see-also"></a>Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
