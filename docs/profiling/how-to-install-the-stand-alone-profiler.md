---
title: "Gewusst wie: Installieren des eigenst&#228;ndigen Profilers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Installieren des eigenständigen Profilers"
  - "Profilerstellungstools, Eigenständige Profiler"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Installieren des eigenst&#228;ndigen Profilers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthält einen eigenständigen, befehlszeilenbasierten Profiler, der ohne Installation der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE ausgeführt werden kann.  Dies ist z. B. der Fall, wenn auf einem Computer keine Entwicklungsumgebung installiert ist oder installiert werden kann.  Beispielsweise sollten Sie keine Entwicklungsumgebung auf einem Produktionswebserver installieren.  
  
> [!NOTE]
>  Empfehlung: Verwenden Sie statt [VSPerfCmd](../profiling/vsperfcmd.md) das Befehlszeilentool [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md), wenn Sie Leistungsdaten für die ASP.NET\-Website mithilfe des eigenständigen Profilers sammeln.  
  
### So installieren Sie den eigenständigen Profiler  
  
1.  Suchen Sie auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Installationsmedium im Verzeichnis mit dem Profilerpfad \\Standalone das Installationsprogramm für den eigenständigen Profiler \(vs\_profiler.exe\), und führen Sie das Programm aus.  
  
2.  Fügen Sie dem Systempfad die Pfade für vsintr.exe und msdis150.dll hinzu.  
  
    > [!NOTE]
    >  Bei der Standardinstallation von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] befinden sich "vsinstr.exe" und "msdis150.dll" im Verzeichnis "\\Programme\\Visual Studio 10\\Team Tools\\Performance Tools".  
  
3.  Geben Sie an der Eingabeaufforderung **VSInstr** ein.  
  
    > [!NOTE]
    >  Wenn die Verwendungsinformationen für vsinstr.exe angezeigt werden, ist alles ordnungsgemäß eingerichtet.  Wenn eine Fehlermeldung mit dem Hinweis ausgegeben wird, dass vsinstr.exe oder eine abhängige Datei nicht gefunden wurde, überprüfen Sie, ob die Pfade wie unter Schritt 2 beschrieben ordnungsgemäß eingerichtet wurden.  
  
4.  Richten Sie den Symbolserver ein, indem Sie die **\_NT\_SYMBOL\_PATH**\-Variable auf **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols** festlegen.  
  
5.  Nachdem Sie den Symbolserver mithilfe der Systemumgebungsvariablen eingerichtet haben, führen Sie die Profilertools für die Befehlszeile an der neuen Eingabeaufforderung aus.  Dadurch werden die neuen Umgebungsvariablen wirksam.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Ausführliche Anweisungen zum Einrichten des Symbolserverpakets finden Sie unter [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Verwenden Sie das Tool [VSPerfReport](../profiling/vsperfreport.md), um die Symbole in der Profilerstellungsdatendatei \(.vsp\) zu serialisieren.  Verwenden Sie die folgenden Schalter: **VSPerfReport \/summary:all \/packsymbols**.  Wenn keine Symbole in der Datendatei enthalten sind, vergewissern Sie sich, dass die \_NT\_SYMBOL\_PATH\-Umgebungsvariable festgelegt wurde.  
  
## Siehe auch  
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)