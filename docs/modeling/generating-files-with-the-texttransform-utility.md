---
title: Generieren von Dateien mit dem Hilfsprogramm "TextTransform" in Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61c71b67c02493ac77a2fd1c21bb47e78122a1d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928658"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"

TextTransform.exe ist ein Befehlszeilentool, das Sie zum Transformieren einer Textvorlage verwenden können. Wenn Sie TextTransform.exe aufrufen, geben Sie den Namen einer Textvorlagendatei als Argument. TextTransform.exe Ruft die Transformations-Engine auf und verarbeitet die Textvorlage. TextTransform.exe wird in der Regel von Skripts aufgerufen. Allerdings ist es nicht in der Regel erforderlich, da Sie Texttransformation in Visual Studio oder im Buildprozess ausführen können.

> [!NOTE]
> Wenn Sie TextTransformation als Teil des Buildvorgangs ausführen möchten, sollten erwägen Sie, die MSBuild-Text-transformationsaufgabe zu verwenden. Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem Visual Studio installiert ist, können Sie auch schreiben eine Anwendung oder ein Visual Studio-Erweiterung, die Textvorlagen transformiert werden können. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe befindet sich im folgenden Verzeichnis:

 **\Programme Dateien (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

für die Professional Edition oder

 **\Programme Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 für die Enterprise Edition.

In früheren Versionen von Visual Studio wird die Datei am folgenden Speicherort gefunden:

**\Programme Dateien (x86) \Common Shared\TextTemplating\{Version}**

wobei {Version}, hängt davon ab, die frühere Version installiert ist.

## <a name="syntax"></a>Syntax

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parameter

|**Argument**|**Beschreibung**|
|-|-|
|`templateName`|Identifiziert den Namen der Vorlagendatei, die Sie transformieren möchten.|

|**Option**|**Beschreibung**|
|-|-|
|**-out** \<Dateiname >|Die Datei, die in der die Ausgabe der Transformation geschrieben wird.|
|**-R** \<Assembly >|Eine Assembly, die zum Kompilieren und Ausführen der Textvorlage verwendet wird.|
|**-u** \<Namespace >|Ein Namespace, der zum Kompilieren von der Vorlage verwendet wird.|
|**-I** \<includedirectory>|Ein Verzeichnis mit den Textvorlagen, die in der Vorlage angegebenen Text enthalten.|
|**-P** \<referencepath>|Ein Verzeichnis an, suchen Sie in die Textvorlage angegebenen Assemblys oder zur Verwendung der **- R** Option.<br /><br /> Beispielsweise wenn Assemblys, die für die Visual Studio-API einschließen möchten, verwenden<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Der Name, die vollständigen Typnamen und die Assembly mit einem anweisungsprozessor, der zum Verarbeiten von benutzerdefinierter Anweisungen innerhalb der Textvorlage verwendet werden kann.|
|**– ein** [ProcessorName]. [ DirectiveName]! \<ParameterName >! \<ParameterValue >|Geben Sie einen Parameterwert für einen anweisungsprozessor. Wenn Sie nur den Parameternamen und-Wert angeben, wird der Parameter für alle anweisungsprozessoren verfügbar sein. Wenn Sie einen anweisungsprozessor angeben, ist der Parameter nur für den angegebenen Prozessor zur Verfügung. Wenn Sie einen Namen der Standarddirektive angeben, ist der Parameter verfügbar sind, nur, wenn die angegebene Richtlinie verarbeitet wird.<br /><br /> Verwenden Sie den Zugriff auf die Parameterwerte von einem Direktivenprozessor oder der Textvorlage [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). Enthalten in einer Textvorlage `hostspecific` in der Template-Anweisung, und rufen Sie die Nachricht auf `this.Host`. Zum Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Geben Sie immer die "!" kennzeichnet, auch wenn Sie den optionalen Prozessor und Direktivennamen weglassen. Zum Beispiel:<br /><br /> `-a !!param!value`|
|**-h**|Enthält die Hilfe.|

## <a name="related-topics"></a>Verwandte Themen

|Aufgabe|Thema|
|-|-|
|Generieren von Dateien in Visual Studio-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
|Schreiben Sie einen Textvorlagenhost, der Sie Textvorlagen aus Ihrer eigenen Anwendung aufrufen kann.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|