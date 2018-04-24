---
title: Anpassen der T4-Texttransformation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 94d04d70192e2730cdf2682a3d2d138089eef891
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-t4-text-transformation"></a>Anpassen der T4-Texttransformation

Textvorlagen sind eine Funktion des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , mit denen Sie Programmcode oder andere Textdateien mithilfe eines Transformationsprozesses zu generieren. Mithilfe von [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], Sie können den Standard-Transformationsprozess ab erweitern, indem Anpassen der Textvorlagen-Direktivenprozessor oder die Textvorlagenhosts.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Das Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md) beschreibt die Funktionsweise der TextTransformation und erläutert die Rolle des Vorlagenhosts und Direktivenprozessoren.

 [Erstellen von benutzerdefinierten T4 Text Vorlage Direktivenprozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md) der Direktivenprozessor verarbeitet Direktiven in der Vorlage aus, wie z. B. `<#@template#>.` es während der Kompilierung der Vorlage ausgeführt wird und Assemblys und andere Ressourcen laden können. Sie können auch Code einfügen, durch die Ressourcen zur Laufzeit geladen wird. Definieren Sie eigene Direktivenprozessors komplizierter, können Sie die Komplexität der Vorlagen reduzieren.

 [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md) beim Schreiben einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungstypen, z. B. ein Befehl oder im Menü der Ereignishandler, die Erweiterung kann mithilfe des Textvorlagendiensts jeder Textvorlage transformieren. Sie können übergeben Parameterdaten in die Vorlage über das Sitzungsobjekt und rufen Sie die Werte aus in der Vorlage mithilfe der `<#@parameter#>` Richtlinie.

 [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md) Wenn der Code der Textvorlage ausgeführt wird, wird der Host ermöglicht den Zugriff auf externe Dateien und der Status der Anwendung. Z. B. auf dem Host, der Texttransformationen ausgeführt, in wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Zugriff ermöglichen dem Projektmappen-Explorer. Es zeigt auch Fehler in das Fenster mit der Fehlermeldung. Wenn Sie Texttransformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der Zugriff auf die Dienste verfügbar sind, in diesem Kontext ermöglicht.

 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung, erwägen Sie die vorhandene Transformation Textdienst, anstatt Ihre eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Verweis

- [Schreiben eine T4-Textvorlage](../modeling/writing-a-t4-text-template.md) stellt die Syntax von Textvorlagendirektiven und Kontrollblöcken bereit.