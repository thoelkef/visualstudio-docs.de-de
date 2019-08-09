---
title: Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f054bd91f16bb7621d4beebe7631a49cb406132e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870470"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts

Der *Textvorlagen-Transformations* Prozess übernimmt eine *Textvorlagen* Datei als Eingabe und erzeugt eine Textdatei als Ausgabe. Sie können die Text Transformations-Engine aus einer Visual Studio-Erweiterung oder aus einer eigenständigen Anwendung, die auf einem Computer ausgeführt wird, auf dem Visual Studio installiert ist, aufgerufen werden. Sie müssen jedoch einen Textvorlagen *Host*bereitstellen. Diese Klasse verbindet die Vorlage mit der Umgebung. Sie sucht nach Ressourcen wie Assemblys und Includedateien und verarbeitet die Ausgabe und Fehlermeldungen.

> [!TIP]
> Wenn Sie ein Paket oder eine Erweiterung schreiben, das in Visual Studio ausgeführt wird, sollten Sie den Textvorlagen Dienst verwenden, anstatt einen eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Von der Verwendung von Textvorlagentransformationen in Serveranwendungen wird abgeraten. Textvorlagentransformationen sollten nur in einem einzelnen Thread verwendet werden. Dies liegt daran, dass die Textvorlagen-Engine eine einzelne AppDomain wieder verwendet, um Vorlagen zu übersetzen, zu kompilieren und auszuführen. Der übersetzte Code ist nicht auf Threadsicherheit hin konzipiert. Die-Engine ist so konzipiert, dass Dateien serialisiert verarbeitet werden, da Sie zur Entwurfszeit in einem Visual Studio-Projekt vorliegen.
>
> Für Lauf Zeit Anwendungen empfiehlt sich die Verwendung von vorverarbeiteten Textvorlagen: siehe [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

Wenn in der Anwendung zur Kompilierzeit korrigierte Vorlagen verwendet werden, ist es einfacher, vorverarbeitete Textvorlagen zu verwenden. Sie können diesen Ansatz auch verwenden, wenn die Anwendung auf einem Computer ausgeführt wird, auf dem Visual Studio nicht installiert ist. Weitere Informationen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Ausführen einer Text Vorlage in der Anwendung

Zum Ausführen einer Textvorlage rufen Sie die ProcessTemplate-Methode von <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> auf:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Die Anwendung muss die Vorlage finden und bereitstellen und die Ausgabe verarbeiten.

 Im-Parameter müssen Sie eine Klasse bereitstellen, die [itexttemplatingenginehost implementiert.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) `host` Diese Methode wird von der Engine aufgerufen.

 Der Host muss in der Lage sein, Fehler zu protokollieren und Verweise auf Assemblys und Includedateien aufzulösen, er muss eine Anwendungsdomäne bereitstellen, in der die Vorlage ausgeführt werden kann, und den entsprechenden Prozessor für jede Direktive aufrufen.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>wird in **Microsoft. VisualStudio. TextTemplating definiert.\* 0. dll**und [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) sind in **Microsoft. VisualStudio. TextTemplating\*. Interfaces definiert. 0. dll**.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Exemplarische Vorgehensweise: Beim Erstellen eines benutzerdefinierten Text](../modeling/walkthrough-creating-a-custom-text-template-host.md) Vorlagen Hosts wird gezeigt, wie Sie einen benutzerdefinierten Textvorlagen Host erstellen, der die Text Vorlagen Funktionalität außerhalb von Visual Studio verfügbar macht.

## <a name="reference"></a>Referenz
 [Itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Verwandte Abschnitte

- [Im Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md) wird beschrieben, wie die Text Transformation funktioniert und welche Teile angepasst werden können.
- Das [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md) -Anweisungs Prozessoren für Textvorlagen bietet eine Übersicht über Textvorlagen-Anweisungs Prozessoren