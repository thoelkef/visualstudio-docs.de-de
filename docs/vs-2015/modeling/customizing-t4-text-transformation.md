---
title: Anpassen der T4-Text Transformation | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654969"
---
# <a name="customizing-t4-text-transformation"></a>Anpassen der T4-Texttransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Text Vorlagen sind eine Funktion von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], die es Ihnen ermöglicht, Programmcode oder andere Textdateien durch einen Transformationsprozess zu generieren. Mithilfe [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] können Sie den Standardvorlagen-Transformationsprozess erweitern, indem Sie den Text Template-Direktivenprozessor oder den Textvorlagen Host anpassen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Der Text Vorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md) Beschreibt die Funktionsweise der Text Transformation und erläutert die Rolle des Vorlagen Hosts und der direktivenprozessoren.

 [Erstellen von benutzerdefinierten T4](../modeling/creating-custom-t4-text-template-directive-processors.md) -Anweisungs Prozessoren für Text Vorlagen Der Direktivenprozessor behandelt Direktiven in ihrer Vorlage, wie z. b. `<#@template#>.` er während der Kompilierung der Vorlage ausgeführt wird, und kann Assemblys und andere Ressourcen laden. Außerdem kann Code eingefügt werden, der zur Laufzeit Ressourcen lädt. Wenn Sie Ihren eigenen Direktivenprozessor definieren, können Sie die Komplexität Ihrer Vorlagen reduzieren.

 [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md) Wenn Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung, z. b. einen Menübefehl oder einen Ereignishandler, schreiben, kann die Erweiterung den Textvorlagen Dienst zum Transformieren beliebiger Textvorlagen verwenden. Sie können Parameterdaten mithilfe des Session-Objekts an die Vorlage übergeben und die Werte in der Vorlage mithilfe der `<#@parameter#>`-Direktive erhalten.

 [Verarbeiten von Text Vorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md) Wenn der Code der Textvorlage ausgeführt wird, bietet der Host Zugriff auf externe Dateien und den Status der Anwendung. Beispielsweise kann der Host, der Text Transformationen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausführt, Zugriff auf den Projektmappen-Explorer bereitstellen. Außerdem werden Fehler im Fenster "Fehlermeldung" angezeigt. Wenn Sie Text Transformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der den Zugriff auf die in diesem Kontext verfügbaren Dienste ermöglicht.

 Wenn Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung schreiben, sollten Sie den vorhandenen Text Transformations Dienst verwenden, anstatt einen eigenen Host zu schreiben. Weitere Informationen finden Sie unter [Aufrufen von Text Transformation in einer vs-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referenz
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)

 Stellt die Syntax von Textvorlagen Direktiven und-Kontroll Blöcken bereit.
