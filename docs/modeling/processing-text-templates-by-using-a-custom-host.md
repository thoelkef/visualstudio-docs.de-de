---
title: "Processing Text Templates by using a Custom Host | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, in application or VS extension"
  - "text templates, custom directive hosts"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Processing Text Templates by using a Custom Host
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim *Textvorlagen\-Transformationsprozess* wird aus einer *Textvorlagendatei* \(Eingabe\) eine Textdatei \(Ausgabe\) erzeugt.  Sie können das Texttransformationsmodul in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung oder einer eigenständigen Anwendung aufrufen, die auf einem Computer mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  Sie müssen jedoch einen *Textvorlagenhost* bereitstellen.  Diese Klasse verbindet die Vorlage mit der Umgebung. Sie sucht nach Ressourcen wie Assemblys und Includedateien und verarbeitet die Ausgabe und Fehlermeldungen.  
  
> [!TIP]
>  Wenn Sie ein Paket oder eine Erweiterung schreiben, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird, verwenden Sie ggf. den Textvorlagendienst, anstatt einen eigenen Host zu schreiben.  Weitere Informationen finden Sie unter [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Von der Verwendung von Textvorlagentransformationen in Serveranwendungen wird abgeraten.  Textvorlagentransformationen sollten nur in einem einzelnen Thread verwendet werden.  Dies liegt daran, dass das Textvorlagenmodul eine einzelne AppDomain wieder verwendet, um Vorlagen zu übersetzen, zu kompilieren und auszuführen.  Der übersetzte Code ist nicht auf Threadsicherheit hin konzipiert.  Das Modul ist für die serielle Verarbeitung von Dateien vorgesehen, so wie dies zur Entwurfszeit in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt der Fall ist.  
>   
>  Verwenden Sie für Laufzeitanwendungen ggf. vorverarbeitete Textvorlagen \(siehe [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md)\).  
  
 Wenn in der Anwendung zur Kompilierzeit korrigierte Vorlagen verwendet werden, ist es einfacher, vorverarbeitete Textvorlagen zu verwenden.  Sie können diesen Ansatz auch verwenden, wenn die Anwendung auf einem Computer ausgeführt wird, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist.  Weitere Informationen finden Sie unter [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Ausführen einer Textvorlage in der Anwendung  
 Zum Ausführen einer Textvorlage rufen Sie die ProcessTemplate\-Methode von <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> auf:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Die Anwendung muss die Vorlage finden und bereitstellen und die Ausgabe verarbeiten.  
  
 Im `host`\-Parameter muss eine Klasse angegeben werden, die <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> implementiert.  Diese Methode wird vom Modul aufgerufen.  
  
 Der Host muss in der Lage sein, Fehler zu protokollieren und Verweise auf Assemblys und Includedateien aufzulösen, er muss eine Anwendungsdomäne bereitstellen, in der die Vorlage ausgeführt werden kann, und den entsprechenden Prozessor für jede Direktive aufrufen.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> ist in **Microsoft.VisualStudio.TextTemplating.\*.0.dll** definiert, und <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> ist in **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll** definiert.  
  
## In diesem Abschnitt  
 [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Veranschaulicht die Erstellung eines benutzerdefinierten Textvorlagenhosts, der die Textvorlagenfunktion außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verfügbar macht.  
  
## Verweis  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## Verwandte Abschnitte  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der Texttransformation und die anpassbaren Teile.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Enthält eine Übersicht über Textvorlagen\-Direktivenprozessoren.