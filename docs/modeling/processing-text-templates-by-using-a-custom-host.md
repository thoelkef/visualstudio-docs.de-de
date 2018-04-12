---
title: Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af3e5b50095b30a912f6de7b67ba8a40f99127f8
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts
Die *Textvorlagentransformation* verarbeiten nimmt eine *Textvorlage* Datei als Eingabe und eine Textdatei als Ausgabe erzeugt. Sie können das Texttransformationsmodul in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Erweiterung oder einer eigenständigen Anwendung aufrufen, die auf einem Computer mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird. Sie müssen jedoch Bereitstellen einer *Textvorlagenhost*. Diese Klasse verbindet die Vorlage mit der Umgebung. Sie sucht nach Ressourcen wie Assemblys und Includedateien und verarbeitet die Ausgabe und Fehlermeldungen.  
  
> [!TIP]
>  Wenn Sie ein Paket oder eine Erweiterung schreiben, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird, verwenden Sie ggf. den Textvorlagendienst, anstatt einen eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Von der Verwendung von Textvorlagentransformationen in Serveranwendungen wird abgeraten. Textvorlagentransformationen sollten nur in einem einzelnen Thread verwendet werden. Dies liegt daran, dass das Textvorlagenmodul eine einzelne AppDomain wieder verwendet, um Vorlagen zu übersetzen, zu kompilieren und auszuführen. Der übersetzte Code ist nicht auf Threadsicherheit hin konzipiert. Das Modul ist für die serielle Verarbeitung von Dateien vorgesehen, so wie dies zur Entwurfszeit in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt der Fall ist.  
>   
>  Für Anwendungen zur Laufzeit, sollten Sie vorverarbeitete Textvorlagen: finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Wenn in der Anwendung zur Kompilierzeit korrigierte Vorlagen verwendet werden, ist es einfacher, vorverarbeitete Textvorlagen zu verwenden. Sie können diesen Ansatz auch verwenden, wenn die Anwendung auf einem Computer ausgeführt wird, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Ausführen einer Textvorlage in der Anwendung  
 Zum Ausführen einer Textvorlage rufen Sie die ProcessTemplate-Methode von <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> auf:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Die Anwendung muss die Vorlage finden und bereitstellen und die Ausgabe verarbeiten.  
  
 Im `host`-Parameter muss eine Klasse angegeben werden, die <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> implementiert. Diese Methode wird vom Modul aufgerufen.  
  
 Der Host muss in der Lage sein, Fehler zu protokollieren und Verweise auf Assemblys und Includedateien aufzulösen, er muss eine Anwendungsdomäne bereitstellen, in der die Vorlage ausgeführt werden kann, und den entsprechenden Prozessor für jede Anweisung aufrufen.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> wird definiert, **Microsoft.VisualStudio.TextTemplating.\*. 0-Dll**, und <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> ist definiert **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0-Dll**.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Veranschaulicht die Erstellung eines benutzerdefinierten Textvorlagenhosts, der die Textvorlagenfunktion außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verfügbar macht.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der Texttransformation und die anpassbaren Teile.  
  
 [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Enthält eine Übersicht über Textvorlagen-Anweisungsprozessoren.