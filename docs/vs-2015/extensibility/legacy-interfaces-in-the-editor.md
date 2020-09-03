---
title: Legacy Schnittstellen im Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180289"
---
# <a name="legacy-interfaces-in-the-editor"></a>Legacyschnittstellen im Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können über Legacy Schnittstellen auf den Visual Studio-Editor zugreifen. Das Visual Studio SDK enthält Adapter, die als *Shims*bezeichnet werden, die diese Schnittstellen für die Interaktion mit dem neuen Editor aktivieren. Dennoch wird empfohlen, dass Sie Ihren Legacy Code aktualisieren, um die neue Editor-API zu verwenden. Der Code funktioniert besser, und Sie können neue Technologien wie die Windows Presentation Foundation (WPF) und die Managed Extensibility Framework (MEF) verwenden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Anpassen des Legacycodes an den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert, wie der Code an den neuen Editor angepasst wird.|  
|[Neues oder verändertes Verhalten mit Editoradaptern](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Erläutert, wie sich das Verhalten der Editor Adapter von denen früherer Versionen des Editors unterscheidet.|  
|[Im Core-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die verschiedenen Komponenten früherer Versionen des Editors.|  
|[Instanziieren des Core-Editors mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Erläutert, wie die Legacy-API verwendet wird, um den Kern-Editor zu instanziieren.|  
|[Editorfactorys](../extensibility/editor-factories.md)|Erläutert, wie editorfactorys mit der Legacy-API verwendet werden.|  
|[Vorgehensweise: Registrieren von Editordateitypen](../extensibility/how-to-register-editor-file-types.md)|Erläutert, wie Sie eine Dateinamenerweiterung mit Ihrem Editor verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editordateityps](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Erläutert, wie ein Kern Editor erstellt und eine Dateinamenerweiterung mit diesem verknüpft wird.|  
|[Vorgehensweise: Angeben von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)|Erläutert, wie Kontext für den Editor bereitgestellt wird.|  
|[Sprachdienste und der Core-Editor](../extensibility/language-services-and-the-core-editor.md)|Erläutert die Interaktionen zwischen einem Sprachdienst und einem Editor.|  
|[Zugriff auf den Textpuffer mit der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Erläutert den Zugriff auf den Text Puffer mithilfe der Legacy-API.|  
|[Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Erläutert, wie Sie mithilfe der Legacy-API auf die Textansicht zugreifen können.|  
|[Anpassen von Codefenstern mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Erläutert, wie Code Fenster mithilfe der Legacy-API angepasst werden.|  
|[Zugriff auf Textschichten mit der Legacy-API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Erläutert den Zugriff auf verschiedene Textebenen mithilfe der Legacy-API.|  
|[Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)|Erläutert, wie Textmarker mithilfe der Legacy-API hinzugefügt werden.|  
|[Anpassen von Editorfarben und -menüs mit der Legacy-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Erläutert, wie Editor-Steuerelemente mithilfe der Legacy-API angepasst werden.|  
|[Verwalten von „Rückgängig machen“ und „Wiederholen“ mit der Legacy-API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Erläutert das Verwalten von Rückgängigmachen und wiederholen mithilfe der Legacy-API.|  
|[Vorgehensweise: Implementieren von „Suchen und Ersetzen“](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Erläutert, wie suchen und ersetzen mithilfe der Legacy-API verwaltet werden.|  
|[Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen](../extensibility/how-to-suppress-file-change-notifications.md)|Erläutert, wie Datei Änderungs Benachrichtigungen unterdrückt werden, indem die Legacy-API verwendet wird.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Erläutert, wie benutzerdefinierte Editoren und Designer erstellt werden.|  
|[Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)|Enthält Links zu Dokumenten über Features, die Anpassungsfunktionen für den Kern-Editor bereitstellen, indem Sie die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Unterstützung für einen Sprachdienst hinzufügen.|  
|[Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)|Erläutert die Verwendung von Schriftarten und Farben mit Legacy Schnittstellen.|
