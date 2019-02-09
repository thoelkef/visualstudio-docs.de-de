---
title: Anpassen der T4-Texttransformation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33f7fd14ff62369de66e4934bf9bb2cf6fd83542
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951552"
---
# <a name="customize-t4-text-transformation"></a>Anpassen der T4-Texttransformation

Textvorlagen sind ein Feature von Visual Studio, mit denen Sie Programmcode oder anderen Textdateien über ein Transformationsprozess generieren können. Mithilfe von [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], Sie können die Standard-Transformationsprozess erweitern, indem Anpassen der Textvorlagen-Direktivenprozessor oder die Textvorlagenhosts.

## <a name="in-this-section"></a>In diesem Abschnitt

 [Das Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md) beschreibt die Funktionsweise der TextTransformation und erläutert die Rolle des Vorlagenhosts und anweisungsprozessoren.

 [Erstellen von benutzerdefinierten T4 Text Vorlage Richtlinie Prozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md) des anweisungsprozessors befasst sich mit den Anweisungen in der Vorlage aus, wie z. B. `<#@template#>.` es ausgeführt wird, während der Kompilierung der Vorlage und Assemblys und andere Ressourcen laden können. Sie können auch Code einfügen, die Ressourcen zur Laufzeit geladen werden. Definieren Sie eigene anweisungsprozessor, können Sie die Komplexität Ihrer Vorlagen reduzieren.

 [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md) , wenn Sie eine Visual Studio-Erweiterung, z. B. ein Menü-Befehl oder Ereignis-Handler schreiben, können die Erweiterung des Textvorlagendiensts transformieren jeder Textvorlage. Sie können Parameterdaten in die Vorlage übergeben, durch die Verwendung des Sitzungsobjekts und rufen Sie die Werte aus, in der Vorlage mit der `<#@parameter#>` Richtlinie.

 [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md) Wenn der Code der Textvorlage ausgeführt wird, stellt der Host Zugriff auf externe Dateien und der Status der Anwendung. Beispielsweise kann der Host, der in Visual Studio Texttransformationen läuft bieten Zugriff auf **Projektmappen-Explorer**. Außerdem werden Fehler im Fenster mit Fehlermeldungen angezeigt. Wenn Sie Texttransformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der Zugriff auf die Dienste verfügbar sind, in diesem Kontext bereitstellt.

 Wenn Sie Visual Studio-Erweiterung schreiben, sollten Sie den vorhandenen Text Transformation-Dienst zu verwenden, anstatt einen eigenen Host. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referenz

- [Schreiben eine T4-Textvorlage](../modeling/writing-a-t4-text-template.md) stellt die Syntax der textvorlagenanweisungen und Kontrollblöcke bereit.