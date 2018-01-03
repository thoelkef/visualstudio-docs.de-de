---
title: "Vorgehensweise: Installieren des eigenständigen Profilers | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bf0c454e649f45975a4d45300923dbd155511136
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Gewusst wie: Installieren des eigenständigen Profilers
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet einen befehlszeilenbasierten, eigenständigen Profiler, der ohne eine Installation der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE ausgeführt werden kann. Diese Situation tritt auf, wenn auf einem Computer keine Entwicklungsumgebung installiert ist oder nicht installiert werden kann. Sie sollten beispielsweise keine Entwicklungsumgebung auf einem Produktionswebserver installieren.  
  
> [!NOTE]
>  Wenn Sie den eigenständigen Profiler verwenden, um Leistungsdaten für die ASP.NET-Website zu erfassen, wird das [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)-Befehlszeilentool statt dem [VSPerfCmd](../profiling/vsperfcmd.md)-Tool empfohlen.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Installieren des eigenständigen Profilers  
  
1.  Suchen Sie den Installer des eigenständigen Profilers („vs_profiler.exe“) auf den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Installationsmedien in dem Verzeichnis, das den Pfad „\Standalone Profiler“ enthält, und führen Sie diesen aus.  
  
2.  Fügen Sie die Pfade für „vsintr.exe“ und „msdis150.dll“ zum Systempfad hinzu.  
  
    > [!NOTE]
    >  In der Standardinstallation von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] befinden sich „vsintr.exe“ und „msdis150.dll“ unter \Programme\Visual Studio 10\Team Tools\Performance Tools.  
  
3.  Geben Sie **VSInstr** in der Eingabeaufforderung ein.  
  
    > [!NOTE]
    >  Wenn die Nutzungsinformationen für „vsinstr.exe“ angezeigt werden, ist alles ordnungsgemäß eingerichtet. Wenn Ihnen ein Fehler angezeigt wird, dass „vsinstr.exe“ oder eine der Abhängigkeiten nicht gefunden werden kann, stellen Sie sicher, dass Sie die Pfade wie in Schritt 2 beschrieben ordnungsgemäß eingerichtet haben.  
  
4.  Richten Sie einen Symbolserver ein, indem Sie die Variable **_NT_SYMBOL_PATH** auf **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols** festlegen.  
  
5.  Nachdem Sie Ihren Symbolserver mithilfe der Umgebungsvariablen des Systems eingerichtet haben, führen Sie die Befehlszeilentools des Profilers über eine neue Eingabeaufforderung aus. Dadurch werden die neuen Umgebungsvariablen wirksam. Geben Sie im Fenster der Eingabeaufforderung folgenden Befehl ein:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Eine ausführliche Anleitung zum Einrichten des Symbolserverpakets finden Sie unter [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Verwenden Sie das [VSPerfReport](../profiling/vsperfreport.md)-Tool, um Ihre Symbole in der Datei für Profilerstellungsdaten (VSP) zu serialisieren. Verwenden Sie die Schalter **VSPerfReport /summary:all /packsymbols**. Wenn Sie keine Symbole in Ihre Datendatei eingefügt haben, stellen Sie sicher, dass Sie die Umgebungsvariable _NT_SYMBOL_PATH festgelegt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)