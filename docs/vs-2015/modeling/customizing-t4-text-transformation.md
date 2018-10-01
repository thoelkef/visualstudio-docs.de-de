---
title: Anpassen der T4-TextTransformation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e304b38979b80c1d67d3f88accdbfa584406c9cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523577"
---
# <a name="customizing-t4-text-transformation"></a>Anpassen der T4-Texttransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anpassen der T4-TextTransformation](https://docs.microsoft.com/visualstudio/modeling/customizing-t4-text-transformation).  
  
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



