---
title: Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9f27d203f317a63049015dbeba073d8ee075e61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428068"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die *Textvorlagen-Transformationsprozess* wird eine *Textvorlage* Datei als Eingabe und erzeugt eine Textdatei, die als Ausgabe. Sie können die Texttransformations-Engine in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterung oder einer eigenständigen Anwendung aufrufen, die auf einem Computer mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird. Sie müssen jedoch Bereitstellen einer *Textvorlagenhost*. Diese Klasse verbindet die Vorlage mit der Umgebung. Sie sucht nach Ressourcen wie Assemblys und Includedateien und verarbeitet die Ausgabe und Fehlermeldungen.  
  
> [!TIP]
> Wenn Sie ein Paket oder eine Erweiterung schreiben, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird, verwenden Sie ggf. den Textvorlagendienst, anstatt einen eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
> Von der Verwendung von Textvorlagentransformationen in Serveranwendungen wird abgeraten. Textvorlagentransformationen sollten nur in einem einzelnen Thread verwendet werden. Dies liegt daran, dass die Textvorlagen-Engine eine einzelne AppDomain wieder verwendet, um Vorlagen zu übersetzen, zu kompilieren und auszuführen. Der übersetzte Code ist nicht auf Threadsicherheit hin konzipiert. Die Engine ist für die serielle Verarbeitung von Dateien vorgesehen, so wie dies zur Entwurfszeit in einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt der Fall ist.  
>   
> Laufzeit-Anwendungen, sollten Sie vorverarbeitete Textvorlagen: finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Wenn in der Anwendung zur Kompilierzeit korrigierte Vorlagen verwendet werden, ist es einfacher, vorverarbeitete Textvorlagen zu verwenden. Sie können diesen Ansatz auch verwenden, wenn die Anwendung auf einem Computer ausgeführt wird, auf dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht installiert ist. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Ausführen einer Textvorlage in der Anwendung  
 Zum Ausführen einer Textvorlage rufen Sie die ProcessTemplate-Methode von <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> auf:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Die Anwendung muss die Vorlage finden und bereitstellen und die Ausgabe verarbeiten.  
  
 Im `host`-Parameter muss eine Klasse angegeben werden, die <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> implementiert. Diese Methode wird von der Engine aufgerufen.  
  
 Der Host muss in der Lage sein, Fehler zu protokollieren und Verweise auf Assemblys und Includedateien aufzulösen, er muss eine Anwendungsdomäne bereitstellen, in der die Vorlage ausgeführt werden kann, und den entsprechenden Prozessor für jede Direktive aufrufen.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> wird definiert, **Microsoft.VisualStudio.TextTemplating.\*. 0.Dll**, und <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> ist definiert **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0.Dll**.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Veranschaulicht die Erstellung eines benutzerdefinierten Textvorlagenhosts, der die Textvorlagenfunktion außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verfügbar macht.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der Texttransformation und die anpassbaren Teile.  
  
 [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Enthält eine Übersicht über Textvorlagen-Direktivenprozessoren.
