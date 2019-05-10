---
title: Generieren von Dateien mit dem Hilfsprogramm "TextTransform" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 607eda7550819e4150f026a0671ed744ba9c10a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427046"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe ist ein Befehlszeilentool, das Sie zum Transformieren einer Textvorlage verwenden können. Wenn Sie TextTransform.exe aufrufen, geben Sie den Namen einer Textvorlagendatei als Argument. TextTransform.exe Ruft die Transformations-Engine auf und verarbeitet die Textvorlage. TextTransform.exe wird in der Regel von Skripts aufgerufen. Allerdings ist es nicht in der Regel erforderlich, da Sie Texttransformation in Visual Studio oder im Buildprozess ausführen können.  
  
> [!NOTE]
> Wenn Sie TextTransformation als Teil des Buildvorgangs ausführen möchten, sollten erwägen Sie, die MSBuild-Text-transformationsaufgabe zu verwenden. Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installiert ist, Sie können auch eine Anwendung schreiben oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterung, die Textvorlagen transformiert werden kann. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe befindet sich im folgenden Verzeichnis:  
  
 **\Programme\Gemeinsame Dateien\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Syntax  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parameter  
  
|**Argument**|**Beschreibung**|  
|------------------|---------------------|  
|`templateName`|Identifiziert den Namen der Vorlagendatei, die Sie transformieren möchten.|  
  
|**Option**|**Beschreibung**|  
|----------------|---------------------|  
|**-out** \<Dateiname >|Die Datei, die in der die Ausgabe der Transformation geschrieben wird.|  
|**-R** \<Assembly >|Eine Assembly, die zum Kompilieren und Ausführen der Textvorlage verwendet wird.|  
|**-u** \<Namespace >|Ein Namespace, der zum Kompilieren von der Vorlage verwendet wird.|  
|**-I** \<includedirectory>|Ein Verzeichnis mit den Textvorlagen, die in der Vorlage angegebenen Text enthalten.|  
|**-P** \<referencepath>|Ein Verzeichnis an, suchen Sie in die Textvorlage angegebenen Assemblys oder zur Verwendung der **- R** Option.<br /><br /> Beispielsweise wenn Assemblys, die für die Visual Studio-API einschließen möchten, verwenden<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Der Name, die vollständigen Typnamen und die Assembly mit einem anweisungsprozessor, der zum Verarbeiten von benutzerdefinierter Anweisungen innerhalb der Textvorlage verwendet werden kann.|  
|**– ein** [ProcessorName]. [ DirectiveName]! \<ParameterName >! \<ParameterValue >|Geben Sie einen Parameterwert für einen anweisungsprozessor. Wenn Sie nur den Parameternamen und-Wert angeben, wird der Parameter für alle anweisungsprozessoren verfügbar sein. Wenn Sie einen anweisungsprozessor angeben, ist der Parameter nur für den angegebenen Prozessor zur Verfügung. Wenn Sie einen Namen der Standarddirektive angeben, ist der Parameter verfügbar sind, nur, wenn die angegebene Richtlinie verarbeitet wird.<br /><br />  Enthalten in einer Textvorlage `hostspecific` in der Template-Anweisung, und rufen Sie die Nachricht auf `this.Host`. Zum Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Geben Sie immer die "!" kennzeichnet, auch wenn Sie den optionalen Prozessor und Direktivennamen weglassen. Zum Beispiel:<br /><br /> `-a !!param!value`|  
|**-h**|Enthält die Hilfe.|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Generieren Sie Dateien in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|  
|Schreiben Sie einen Textvorlagenhost, der Sie Textvorlagen aus Ihrer eigenen Anwendung aufrufen kann.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|
