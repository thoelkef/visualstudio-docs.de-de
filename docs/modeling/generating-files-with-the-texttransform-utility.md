---
title: Generieren von Dateien mit dem Hilfsprogramm &quot;TextTransform&quot; | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"
TextTransform.exe ist ein Befehlszeilentool, mit denen Sie eine Textvorlage transformieren können. Wenn Sie TextTransform.exe aufrufen, geben Sie den Namen einer Textvorlagendatei als Argument. TextTransform.exe Ruft das Texttransformationsmodul auf und verarbeitet die Textvorlage. TextTransform.exe wird normalerweise von Skripts aufgerufen werden. Allerdings ist jedoch nicht in der Regel erforderlich, da Sie Texttransformation in Visual Studio oder im Buildprozess ausführen können.  
  
> [!NOTE]
>  Wenn Sie TextTransformation als Teil des Buildprozesses ausführen möchten, sollten erwägen Sie, die MSBuild-Texttransformationsaufgabe zu verwenden. Weitere Informationen finden Sie unter [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert ist, Sie können auch eine Anwendung schreiben oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung, die Textvorlagen transformieren kann. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe befindet sich im folgenden Verzeichnis:  
  
 **\Programme\Gemeinsame Dateien\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Syntax  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parameter  
  
|**Argument**|**Beschreibung**|  
|------------------|---------------------|  
|`templateName`|Gibt den Namen der Vorlagendatei, die Sie transformieren möchten.|  
  
|**Option**|**Beschreibung**|  
|----------------|---------------------|  
|**-out** \<Dateiname >|Die Datei, die die Ausgabe der Transformation geschrieben wird.|  
|**-R** \<Assembly >|Eine Assembly kompilieren und Ausführen der Textvorlage verwendet.|  
|**-u** \<Namespace >|Ein Namespace, der zum Kompilieren der Vorlage verwendet wird.|  
|**-** \<Includedirectory >|Ein Verzeichnis, die in der angegebenen Textvorlage enthaltenen Textvorlagen enthält.|  
|**P -** \<Referencepath >|Ein Verzeichnis zum Suchen nach in der Textvorlage angegebenen Assemblys oder zum Verwenden der **- R** Option.<br /><br /> Verwenden Sie z. B. zum Einschließen von Assemblys, die für die Visual Studio-API<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**dp -** \<ProcessorName >!\< ClassName >! \<AssemblyName | codeBase >|Der Name, die vollständigen Typnamen und die Assembly mit einem Direktivenprozessor, der verwendet werden kann, um benutzerdefinierte Direktiven innerhalb der Textvorlage zu verarbeiten.|  
|**– ein** [ProcessorName]! [ DirectiveName]! \<ParameterName >! \<ParameterValue >|Geben Sie einen Parameterwert für einen Direktivenprozessor. Wenn Sie nur den Parameternamen und den Wert angeben, wird der Parameter für alle Direktivenprozessoren verfügbar sein. Wenn Sie einen Direktivenprozessor angeben, ist der Parameter nur für den angegebenen Prozessor verfügbar. Wenn Sie einen Direktivennamen angeben, ist der Parameter verfügbar, nur, wenn die angegebene Direktive verarbeitet wird.<br /><br /> Verwenden Sie die Parameterwerte von einem Direktivenprozessor oder einer Textvorlage Zugriff <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> In einer Textvorlage enthalten `hostspecific` in der Template-Direktive und rufen Sie die Nachricht auf `this.Host`. Zum Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Geben Sie immer die '!' markiert, auch wenn Sie die optionale Prozessor- und Direktivennamen weglassen. Zum Beispiel:<br /><br /> `-a !!param!value`|  
|**-h**|Enthält die Hilfe.|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Generieren Sie Dateien in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|  
|Schreiben Sie einen Textvorlagenhost, der Ihnen ermöglicht, Textvorlagen von Ihrer eigenen Anwendung aufzurufen.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|
