---
title: Legacy-Schnittstellen im Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64e867430c2ae55f530bdb66844240a887bd5545
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-interfaces-in-the-editor"></a>Legacy-Schnittstellen im Editor
Sie können die Visual Studio-Editor von legacy-Schnittstellen zugreifen. Das Visual Studio SDK enthält Adapter, die genannte *Shims*, die diese Schnittstellen für die Interaktion mit dem neuen Editor ermöglichen. Dennoch wird empfohlen, dass Sie Ihren Legacycode, um den neuen Editor API aktualisieren. Codes bieten eine bessere Leistung, und Sie können neue Technologien wie Windows Presentation Foundation (WPF) und Managed Extensibility Framework (MEF) verwenden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Anpassen von Legacycode auf den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert, wie Code an den neuen Editor angepasst werden kann.|  
|[Neue oder geänderte Verhalten mit Editor-Adaptern](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Erläutert, wie das Verhalten der Editor-Adapter von früheren Versionen des Editors unterscheidet.|  
|[In der Core-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die verschiedenen Komponenten von früheren Versionen des Editors an.|  
|[Instanziieren den Core-Editor mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Es wird erläutert, wie die legacy-API verwenden, um die Core-Editor zu instanziieren.|  
|[Editor-Factorys](../extensibility/editor-factories.md)|Erläutert das editorfactorys mit legacy-API verwenden.|  
|[Vorgehensweise: Registrieren von Dateitypen-Editor](../extensibility/how-to-register-editor-file-types.md)|Erläutert, wie eine Dateinamenerweiterung mit Editor verknüpft.|  
|[Exemplarische Vorgehensweise: Erstellen eines Kern-Editors, und registrieren einen Dateityp-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Erläutert, wie einen Kern-Editor erstellen und eine Dateinamenerweiterung zu verknüpfen.|  
|[Vorgehensweise: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)|Erläutert die Kontext für den Editor bereitstellt.|  
|[Language-Dienste und die Core-Editor](../extensibility/language-services-and-the-core-editor.md)|Erläutert die Interaktionen zwischen einen Sprachdienst und eines Editors an.|  
|[Zugreifen auf den Textpuffer mithilfe der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Erläutert den Textpuffer über die legacy-API zugreifen.|  
|[Zugreifen auf TheText Ansicht über die Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Erläutert die Textansicht über die legacy-API zugreifen.|  
|[Anpassen von Code-Fenster mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Erläutert das Codefenster anpassen, indem Sie die legacy-API verwenden.|  
|[Zugreifen auf Textebenen über die Legacy-API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Erläutert die unterschiedliche Ebenen von Text mithilfe der legacy-API zugreifen.|  
|[Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)|Erläutert, wie Text Marker hinzufügen, über die legacy-API.|  
|[Anpassen von Editor-Steuerelemente und Menüs, über die Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Erläutert das Editor-Steuerelemente anpassen, indem Sie die legacy-API verwenden.|  
|[Verwalten von rückgängig und wiederholen, über die Legacy-API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Erläutert das Verwalten zum Rückgängigmachen und wiederholen über die legacy-API.|  
|[Vorgehensweise: Implementieren von Suchen und Ersetzen Sie Mechanismus](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Erläutert die Verwaltung von Suchen und ersetzen, indem Sie die legacy-API.|  
|[Vorgehensweise: Dateiänderungsbenachrichtigungen unterdrücken](../extensibility/how-to-suppress-file-change-notifications.md)|Erläutert das Unterdrücken von dateiänderungsbenachrichtigungen über die legacy-API.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Erläutert das Erstellen von benutzerdefinierten Editoren und Designern.|  
|[Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)|Enthält Links zu Dokumenten über Funktionen, die Anpassung ermöglichen die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor durch Hinzufügen der Unterstützung für einen Sprachdienst.|  
|[Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)|Erläutert das Verwenden von Schriftarten und Farben mit legacy-Schnittstellen.|