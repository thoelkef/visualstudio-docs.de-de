---
title: Anpassen der T4-TextTransformation | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ea2881cfebaf10d7a72e8651214cf3a6f64debae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958737"
---
# <a name="customizing-t4-text-transformation"></a>Anpassen der T4-Texttransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textvorlagen sind ein Feature von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , mit denen Sie Programmcode oder anderen Textdateien über ein Transformationsprozess zu generieren. Mithilfe von [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], Sie können die Standard-Transformationsprozess erweitern, indem Anpassen der Textvorlagen-Direktivenprozessor oder die Textvorlagenhosts.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md)  
 Beschreibt die Funktionsweise der TextTransformation und erläutert die Rolle des Vorlagenhosts und anweisungsprozessoren.  
  
 [Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Der anweisungsprozessor befasst sich mit den Anweisungen in der Vorlage aus, wie z. B. `<#@template#>.` es ausgeführt wird, während der Kompilierung der Vorlage und Assemblys und andere Ressourcen laden können. Sie können auch Code einfügen, die Ressourcen zur Laufzeit geladen werden. Definieren Sie eigene anweisungsprozessor, können Sie die Komplexität Ihrer Vorlagen reduzieren.  
  
 [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungstypen, z. B. ein Menü-Befehl oder Ereignis-Handler, die Erweiterung kann mithilfe des Textvorlagendiensts beliebiger Textvorlagen transformieren. Sie können Parameterdaten in die Vorlage übergeben, durch die Verwendung des Sitzungsobjekts und rufen Sie die Werte aus, in der Vorlage mit der `<#@parameter#>` Richtlinie.  
  
 [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Wenn der Code der Textvorlage ausgeführt wird, stellt der Host Zugriff auf externe Dateien und der Status der Anwendung bereit. Z. B. auf dem Host, der Texttransformationen ausgeführt, in wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] können ermöglichen den Zugriff auf den Projektmappen-Explorer. Außerdem werden Fehler im Fenster mit Fehlermeldungen angezeigt. Wenn Sie Texttransformationen in einem anderen Kontext ausführen möchten, können Sie einen eigenen Host definieren, der Zugriff auf die Dienste verfügbar sind, in diesem Kontext bereitstellt.  
  
 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterung, erwägen Sie die vorhandene Transformation Textdienst, anstatt einen eigenen Host. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Referenz  
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)  
  
 Enthält die Syntax der textvorlagenanweisungen und Kontrollblöcken.
