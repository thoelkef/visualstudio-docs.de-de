---
title: Generieren von Dateien mit dem Hilfsprogramm "TextTransform"
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f224419cd92b760d71045859a13887a83115b987
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606094"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"

TextTransform.exe ist ein Befehlszeilentool, das Sie zum Transformieren einer Textvorlage verwenden können. Wenn Sie TextTransform.exe aufrufen, geben Sie den Namen einer Textvorlagendatei als Argument. TextTransform.exe Ruft die Transformations-Engine auf und verarbeitet die Textvorlage. TextTransform.exe wird in der Regel von Skripts aufgerufen. Allerdings ist es nicht in der Regel erforderlich, da Sie Texttransformation in Visual Studio oder im Buildprozess ausführen können.

> [!NOTE]
> Wenn Sie TextTransformation als Teil des Buildvorgangs ausführen möchten, sollten erwägen Sie, die MSBuild-Text-transformationsaufgabe zu verwenden. Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem Visual Studio installiert ist, können Sie auch schreiben eine Anwendung oder ein Visual Studio-Erweiterung, die Textvorlagen transformiert werden können. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe befindet sich im folgenden Verzeichnis:
 
::: moniker range=">=vs-2019"

**\Programme (x86) \Microsoft Visual studio\2019\professional\common7\ide**

für Professional Edition oder

**\Programme (x86) \Microsoft Visual studio\2019\enterprise\common7\ide**

für Enterprise Edition.

::: moniker-end
 
::: moniker range="vs-2017"

**\Programme Dateien (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

für Professional Edition oder

**\Programme Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

für Enterprise Edition.

In früheren Versionen von Visual Studio wird die Datei am folgenden Speicherort gefunden:

**\Programme Dateien (x86) \Common Shared\TextTemplating\{Version}**

wobei {Version}, hängt davon ab, die frühere Version installiert ist.

::: moniker-end

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
|**– ein** [ProcessorName]. [ DirectiveName]! \<ParameterName >! \<ParameterValue >|Geben Sie einen Parameterwert für einen anweisungsprozessor. Wenn Sie nur den Parameternamen und-Wert angeben, wird der Parameter für alle anweisungsprozessoren verfügbar sein. Wenn Sie einen anweisungsprozessor angeben, ist der Parameter nur für den angegebenen Prozessor zur Verfügung. Wenn Sie einen Namen der Standarddirektive angeben, ist der Parameter verfügbar sind, nur, wenn die angegebene Richtlinie verarbeitet wird.<br /><br /> Verwenden Sie den Zugriff auf die Parameterwerte von einem Direktivenprozessor oder der Textvorlage [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). Enthalten in einer Textvorlage `hostspecific` in der Template-Anweisung, und rufen Sie die Nachricht auf `this.Host`. Zum Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Geben Sie immer die "!" kennzeichnet, auch wenn Sie den optionalen Prozessor und Direktivennamen weglassen. Zum Beispiel:<br /><br /> `-a !!param!value`|
|**-h**|Enthält die Hilfe.|

## <a name="related-topics"></a>Verwandte Themen

|Aufgabe|Thema|
|-|-|
|Generieren von Dateien in Visual Studio-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
|Schreiben Sie einen Textvorlagenhost, der Sie Textvorlagen aus Ihrer eigenen Anwendung aufrufen kann.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|
