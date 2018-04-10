---
title: Generieren von Dateien mit dem Hilfsprogramm "TextTransform" in Visual Studio | Microsoft Docs
ms.date: 03/22/2018
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5ecc5af3c37889bc79dc5978c33caf8249433978
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"

TextTransform.exe ist ein Befehlszeilentool, mit denen Sie eine Textvorlage transformieren können. Wenn Sie TextTransform.exe aufrufen, geben Sie den Namen des eine Textvorlagendatei als Argument. TextTransform.exe Ruft das Texttransformationsmodul und verarbeitet die Textvorlage. TextTransform.exe wird normalerweise von Skripts aufgerufen. Allerdings ist es nicht in der Regel erforderlich, da Sie in Visual Studio oder im Buildprozess TextTransformation ausführen können.

> [!NOTE]
> Wenn Sie TextTransformation als Teil des Buildprozesses ausführen möchten, sollten erwägen Sie, die MSBuild-Text-transformationsaufgabe zu verwenden. Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert ist, Sie können auch eine Anwendung schreiben oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung, die von Textvorlagen transformiert werden kann. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe befindet sich im folgenden Verzeichnis:

 **\Programme Dateien (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

für die Professional Edition oder

 **\Programme Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 für die Enterprise Edition.

In früheren Versionen von Visual Studio befindet sich die Datei an folgendem Speicherort:

**\Programme Dateien (x86) \Common Shared\TextTemplating\{Version}**

wobei {Version}, hängt davon ab, die frühere Version installiert ist.

## <a name="syntax"></a>Syntax

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parameter

|**Argument**|**Beschreibung**|
|------------------|---------------------|
|`templateName`|Identifiziert den Namen der Vorlagendatei, die transformiert werden sollen.|

|**Option**|**Beschreibung**|
|----------------|---------------------|
|**-out** \<Dateiname >|Die Datei, die in die Ausgabe der Transformation geschrieben wird.|
|**-r** \<assembly>|Eine Assembly, die für das Kompilieren und Ausführen der Textvorlage verwendet wird.|
|**u -** \<Namespace >|Ein Namespace, der zum Kompilieren der Vorlage verwendet wird.|
|**-I** \<includedirectory>|Ein Verzeichnis, das die Textvorlagen enthalten in der Vorlage angegebenen Text enthält.|
|**-P** \<referencepath>|Eine zu durchsuchende Verzeichnis an in der Textvorlage angegebenen Assemblys oder zur Verwendung der **- R** Option.<br /><br /> Verwenden Sie z. B. zum Einschließen von Assemblys, die für die Visual Studio-API verwendet<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Der Name, die vollständigen Typnamen und die Assembly mit einem Direktivenprozessor, der zum Verarbeiten von benutzerdefinierter Richtlinien in der Vorlage "Text" verwendet werden kann.|
|**– ein** [ProcessorName]! [ DirectiveName]! \<ParameterName >! \<%ParameterValue >|Geben Sie einen Parameterwert für einen Direktivenprozessor. Wenn Sie nur den Parameternamen und den Wert angeben, wird der Parameter für alle Direktivenprozessoren verfügbar sein. Wenn Sie einen Direktivenprozessor angeben, ist der Parameter nur für den angegebenen Prozessor zur Verfügung. Wenn Sie einen Richtlinie Namen angeben, ist der Parameter zur Verfügung, nur, wenn die angegebene Direktive verarbeitet wird.<br /><br /> Verwenden Sie den Zugriff auf die Parameterwerte aus einem Direktivenprozessor oder die Vorlage "Text" [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). In einer Textvorlage enthalten `hostspecific` in der Template-Direktive und rufen Sie die Nachricht auf `this.Host`. Zum Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`<br /><br /> Geben Sie immer die "!" markiert, auch wenn Sie die optionale Prozessor- und Anweisungsnamen weglassen. Zum Beispiel:<br /><br /> `-a !!param!value`|
|**-h**|Enthält die Hilfe.|

## <a name="related-topics"></a>Verwandte Themen

|Aufgabe|Thema|
|----------|-----------|
|Generieren Sie Dateien in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
|Schreiben Sie einen Textvorlagenhost, der Ihnen ermöglicht, Textvorlagen von Ihrer eigenen Anwendung aufrufen.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|