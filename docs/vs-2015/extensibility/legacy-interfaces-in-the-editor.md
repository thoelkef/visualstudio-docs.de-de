---
title: Legacy-Schnittstellen im Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48e468a8b0378e33f8c3f371b5da8dc5fd7b8758
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271569"
---
# <a name="legacy-interfaces-in-the-editor"></a>Legacy-Schnittstellen im Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Visual Studio-Editor von legacy-Schnittstelle zugreifen. Visual Studio SDK umfasst Adapter, die als bekannt *Shims*, die es ermöglichen, diese Schnittstellen für die Interaktion mit den neuen Editor. Dennoch wird empfohlen, dass Sie Ihren Legacycode Verwendung des neuen Editors für API aktualisieren. Ihr Code bieten eine bessere Leistung und Sie können neue Technologien wie Windows Presentation Foundation (WPF) und das Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Anpassen des Legacycodes an den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert, wie Sie Ihren Code an den neuen Editor anpassen.|  
|[Neues oder verändertes Verhalten mit Editoradaptern](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Erläutert, wie sich das Verhalten der Editor für Adapter aus, die von früheren Versionen des Editors unterscheidet.|  
|[Im Core-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die verschiedenen Komponenten von früheren Versionen des Editors.|  
|[Instanziieren des Core-Editors mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Es wird erläutert, wie die legacy-API zu verwenden, um die Kern-Editor zu instanziieren.|  
|[Editorfactorys](../extensibility/editor-factories.md)|Erläutert, wie Sie editorfactorys mit der legacy-API verwenden können.|  
|[Vorgehensweise: Registrieren von Editordateitypen](../extensibility/how-to-register-editor-file-types.md)|Erläutert, wie eine Dateinamenerweiterung mit den Editor zu verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editordateityps](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Erläutert, wie einen Kern-Editor erstellen und verknüpfen eine Dateinamenerweiterung, darauf.|  
|[Vorgehensweise: Angeben von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)|Erläutert das Kontext für den Editor bereitzustellen.|  
|[Sprachdienste und der Core-Editor](../extensibility/language-services-and-the-core-editor.md)|Erläutert, die Interaktionen zwischen einem Sprachdienst und einen Editor.|  
|[Zugriff auf den Textpuffer mit der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Erläutert, wie auf den Textpuffer mithilfe der legacy-API.|  
|[Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Erläutert, wie die Ansicht für den Zugriff mithilfe der legacy-API auf.|  
|[Anpassen von Codefenstern mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Erläutert das Codefenster anpassen, indem Sie mit der legacy-API.|  
|[Zugriff auf Textschichten mit der Legacy-API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Erläutert, wie auf verschiedenen Ebenen von Text mithilfe der legacy-API.|  
|[Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)|Erläutert das Textmarkierungen hinzufügen, indem Sie mit der legacy-API.|  
|[Anpassen von Editorfarben und -menüs mit der Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Erläutert das Editor-Steuerelemente anpassen, indem Sie mit der legacy-API.|  
|[Verwalten von „Rückgängig machen“ und „Wiederholen“ mit der Legacy-API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Erläutert, wie "Rückgängig" zu verwalten und wiederherstellen, indem Sie mit der legacy-API.|  
|[Vorgehensweise: Implementieren von „Suchen und Ersetzen“](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Erläutert, wie zum Verwalten von Suchen und ersetzen, indem Sie die legacy-API.|  
|[Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen](../extensibility/how-to-suppress-file-change-notifications.md)|Erläutert das dateiänderungsbenachrichtigungen zu unterdrücken, indem Sie mit der legacy-API.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Erläutert das Erstellen von benutzerdefinierten Editoren und Designern.|  
|[Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)|Enthält Links zu Dokumenten über Features, die der Anpassungsfunktionen zum Bereitstellen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durch Hinzufügen von Unterstützung für einen Sprachdienst-Kern-Editor.|  
|[Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)|Erläutert, wie Schriftarten und Farben mit legacy-Schnittstellen.|

