---
title: Erstellen von Dateien mit dem textTransform-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666097"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generieren von Dateien mit dem Hilfsprogramm "TextTransform"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe ist ein Befehlszeilen Tool, mit dem Sie eine Textvorlage transformieren können. Wenn Sie TextTransform.exe aufzurufen, geben Sie den Namen einer Textvorlagen Datei als Argument an. TextTransform.exe die Text-Transformations-Engine aufruft und die Textvorlage verarbeitet. TextTransform.exe wird in der Regel aus Skripts aufgerufen. Dies ist jedoch in der Regel nicht erforderlich, da Sie die Text Transformation entweder in Visual Studio oder im Buildprozess durchführen können.

> [!NOTE]
> Wenn Sie die Text Transformation als Teil eines Buildprozesses durchführen möchten, sollten Sie die MSBuild-Text Transformations Aufgabe verwenden. Weitere Informationen finden Sie unter [Code Generierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md). Auf einem Computer, auf dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installiert ist, können Sie auch eine Anwendung oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung schreiben, mit der Textvorlagen transformiert werden können. Weitere Informationen finden Sie unter [Verarbeiten von Text Vorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe befindet sich im folgenden Verzeichnis:

 **\Programme\Gemeinsame Dateien\Microsoft shared\texttemplating\11.0**

## <a name="syntax"></a>Syntax

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Parameter

|**Argument**|**Beschreibung**|
|------------------|---------------------|
|`templateName`|Gibt den Namen der Vorlagen Datei an, die Sie transformieren möchten.|

|**Option**|**Beschreibung**|
|----------------|---------------------|
|**-out** \<filename>|Die Datei, in die die Ausgabe der Transformation geschrieben wird.|
|**-r** \<assembly>|Eine Assembly, die zum Kompilieren und Ausführen der Textvorlage verwendet wird.|
|**-u**\<namespace>|Ein Namespace, der zum Kompilieren der Vorlage verwendet wird.|
|**-I**\<includedirectory>|Ein Verzeichnis, das die in der angegebenen Textvorlage enthaltenen Textvorlagen enthält.|
|**-P**\<referencepath>|Ein Verzeichnis, in dem nach Assemblys gesucht werden soll, die in der Textvorlage oder der Option **-r** angegeben sind.<br /><br /> Um z. b. für die Visual Studio-API verwendete Assemblys einzuschließen, verwenden Sie<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Der Name, der vollständige Typname und die Assembly eines direktivenprozessors, der zum Verarbeiten von benutzerdefinierten Direktiven in der Textvorlage verwendet werden kann.|
|**-a** [processorname]! [directivename]! \<parameterName> !\<parameterValue>|Geben Sie einen Parameterwert für einen Direktivenprozessor an. Wenn Sie nur den Parameternamen und den Wert angeben, ist der Parameter für alle direktivenprozessoren verfügbar. Wenn Sie einen Direktivenprozessor angeben, ist der-Parameter nur für den angegebenen Prozessor verfügbar. Wenn Sie einen Direktivennamen angeben, ist der-Parameter nur verfügbar, wenn die angegebene Direktive verarbeitet wird.<br /><br />  Fügen Sie in einer Textvorlage `hostspecific` in die Template-Direktive ein, und rufen Sie die Meldung für auf `this.Host` . Beispiel:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Geben Sie immer die Zeichen "!" ein, auch wenn Sie die optionalen Prozessor-und Direktivennamen weglassen. Beispiel:<br /><br /> `-a !!param!value`|
|**-h**|Stellt Hilfe bereit.|

## <a name="related-topics"></a>Zugehörige Themen

|Aufgabe|Thema|
|----------|-----------|
|Generieren Sie Dateien in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Schreiben Sie Direktivenprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
|Schreiben Sie einen Textvorlagen Host, mit dem Sie Textvorlagen aus ihrer eigenen Anwendung aufrufen können.|[Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)|
