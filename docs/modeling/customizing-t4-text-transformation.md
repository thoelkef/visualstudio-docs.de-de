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
ms.openlocfilehash: 03acd2b989f3403c04d7a0bacdf1fb3e6e6213db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251838"
---
# <a name="customize-t4-text-transformation"></a>Anpassen der T4-Texttransformation

Text Vorlagen sind eine Funktion von Visual Studio, die es Ihnen ermöglicht, Programmcode oder andere Textdateien durch einen Transformationsprozess zu generieren. Mithilfe [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]von können Sie den standardmäßigen Vorlagen Transformationsprozess erweitern, indem Sie den Text Template-Direktivenprozessor oder den Textvorlagen Host anpassen.

## <a name="in-this-section"></a>In diesem Abschnitt

 [Der Text Vorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md) Beschreibt die Funktionsweise der Text Transformation und erläutert die Rolle des Vorlagen Hosts und der direktivenprozessoren.

 [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md) -Anweisungs Prozessoren für Text Vorlagen Der Direktivenprozessor verarbeitet Anweisungen in der Vorlage, z `<#@template#>.` . b. während der Kompilierung der Vorlage, und kann Assemblys und andere Ressourcen laden. Außerdem kann Code eingefügt werden, der zur Laufzeit Ressourcen lädt. Wenn Sie Ihren eigenen Direktivenprozessor definieren, können Sie die Komplexität Ihrer Vorlagen reduzieren.

 [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md) Wenn Sie eine Visual Studio-Erweiterung, z. b. einen Menübefehl oder einen Ereignishandler, schreiben, kann die Erweiterung den Textvorlagen Dienst zum Transformieren beliebiger Textvorlagen verwenden. Sie können Parameterdaten mithilfe des Session-Objekts an die Vorlage übergeben und die Werte in der Vorlage mithilfe der `<#@parameter#>` -Direktive erhalten.

 [Verarbeiten von Text Vorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md) Wenn der Code der Textvorlage ausgeführt wird, bietet der Host Zugriff auf externe Dateien und den Status der Anwendung. Beispielsweise kann der Host, auf dem Text Transformationen in Visual Studio ausgeführt werden, Zugriff auf **Projektmappen-Explorer**bereitstellen. Außerdem werden Fehler im Fenster "Fehlermeldung" angezeigt. Wenn Sie Text Transformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der den Zugriff auf die in diesem Kontext verfügbaren Dienste ermöglicht.

 Wenn Sie eine Visual Studio-Erweiterung schreiben, sollten Sie die Verwendung des vorhandenen Text Transformations Diensts in Erwägung gezogen, anstatt einen eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referenz

- [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md) stellt die Syntax von Textvorlagen Direktiven und Kontroll Blöcken bereit.