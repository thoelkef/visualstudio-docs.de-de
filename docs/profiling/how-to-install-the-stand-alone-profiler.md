---
title: 'Vorgehensweise: Installieren des eigenständigen Profilers | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 949787ae06d9599f0132c15a0205f034419a312d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928597"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Vorgehensweise: Installieren des eigenständigen Profilers
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet einen befehlszeilenbasierten, eigenständigen Profiler, der ohne eine Installation der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE ausgeführt werden kann. Diese Situation tritt auf, wenn auf einem Computer keine Entwicklungsumgebung installiert ist oder nicht installiert werden kann. Sie sollten beispielsweise keine Entwicklungsumgebung auf einem Produktionswebserver installieren.  
  
> [!NOTE]
>  Wenn Sie den eigenständigen Profiler verwenden, um Leistungsdaten für eine ASP.NET-Website zu erfassen, wird das [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)-Befehlszeilentool statt dem [VSPerfCmd](../profiling/vsperfcmd.md)-Tool empfohlen.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Installieren des eigenständigen Profilers  

1. Laden Sie die [Leistungstools für Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio-2017) herunter.

1. Suchen Sie den Installer für den eigenständigen Profiler (*vs_standaloneprofiler.exe*) dort, wo Sie die heruntergeladenen Leistungstools gespeichert haben, und führen Sie Ihn aus.
  
2. Fügen Sie die Pfade für *vsintr.exe* und *msdis150.dll* zum Systempfad hinzu.  
  
   > [!NOTE]
   >  Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. 
  
3. Geben Sie **VSInstr** in der Eingabeaufforderung ein.  
  
   > [!NOTE]
   >  Wenn die Nutzungsinformationen für „vsinstr.exe“ angezeigt werden, ist alles ordnungsgemäß eingerichtet. Wenn Ihnen ein Fehler angezeigt wird, dass „vsinstr.exe“ oder eine der Abhängigkeiten nicht gefunden werden kann, stellen Sie sicher, dass Sie die Pfade wie in Schritt 2 beschrieben ordnungsgemäß eingerichtet haben.  
  
4. Richten Sie den Symbolserver ein, indem Sie die Variable **_NT_SYMBOL_PATH** auf **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols** festlegen.  
  
5. Nachdem Sie Ihren Symbolserver mithilfe der Umgebungsvariablen des Systems eingerichtet haben, führen Sie die Befehlszeilentools des Profilers über eine neue Eingabeaufforderung aus. Dadurch werden die neuen Umgebungsvariablen wirksam. Geben Sie im Fenster der Eingabeaufforderung folgenden Befehl ein:  
  
    **start %COMSPEC%**  
  
   > [!NOTE]
   >  Eine ausführliche Anleitung zum Einrichten des Symbolserverpakets finden Sie unter [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Verwenden Sie das [VSPerfReport](../profiling/vsperfreport.md)-Tool, um Ihre Symbole in der Datei für Profilerstellungsdaten (VSP) zu serialisieren. Verwenden Sie die Schalter **VSPerfReport /summary:all /packsymbols**. Wenn Sie keine Symbole in Ihre Datendatei eingefügt haben, stellen Sie sicher, dass Sie die Umgebungsvariable _NT_SYMBOL_PATH festgelegt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Sampling](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentierung](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications)   
 [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)