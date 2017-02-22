---
title: "Erstellen von Projekttypen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Neue Projekttypen"
  - "Projekte [Visual Studio SDK] neue Projekttypen"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch die Erstellung eines neuen Projekts. Um einen neuen Projekttyp erstellen möchten, müssen Sie einige Konzepte verstehen, und schließen eine Reihe von Schritten. Die folgenden Themen enthalten eine Übersicht über Projekttypen erstellen.  
  
## In diesem Abschnitt  
 [Projekt Typ Designentscheidungen](../../extensibility/internals/project-type-design-decisions.md)  
 Erläutert die Artikel, projektdauerhaftigkeit\-Datei, und Engagement Mechanic Designentscheidungen, die Sie erstellen, bevor ein neuer Projekttyp erstellen.  
  
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Bietet eine Übersicht über die Schritte, die Sie befolgen müssen, um einen neuen Projekttyp zu erstellen, der Aufgaben bei der Programmierung als Code bearbeiten und kompilieren, erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.  
  
 [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Enthält Informationen zum Bereitstellen und verwenden Sie eine Projekt\-Factory zum Erstellen von Instanzen eines neuen Projekts.  
  
 [Registrieren einen Projekttyp](../../extensibility/internals/registering-a-project-type.md)  
 Enthält Codebeispiele von Anweisungen aus der Registrierung, die Standardpfade und Daten sowie eine Tabelle, die Einträge aus der Registrierungsskript für jede Anweisung enthalten.  
  
 [Projekt\-Persistenz](../../extensibility/internals/project-persistence.md)  
 Erläutert die Verwendung der `IPersistFileFormat` \-Datei und nicht\-Datei\-basierten Projektobjekte beibehalten werden.  
  
 [Verwenden von MSBuild](../../extensibility/internals/using-msbuild.md)  
 Beschreibt, wie der Projekttyp der [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] Buildmoduls zum Erstellen von Benutzern ermöglichen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und in der Befehlszeile.  
  
## Verwandte Abschnitte  
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Erläutert die Architektur von mithilfe von Tools wie z. B. die **Objektkatalog** und **Klassenansicht** Fenster. Beschreibt die Schnittstellen und Methoden, die verwendet werden, um das Durchsuchen eingebetteter Objekte in einem VSPackage implementieren.  
  
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Erläutert die Bedeutung, die Projekte spielen bei der Bestimmung der Editor verwendet wird, wenn ein Projektelement geöffnet wird und wie die Ressourcen des Projekts geändert werden können.  
  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Zeigt, wie Sie Ihr VSPackage eigene eindeutige Identität und wie Sie Ihre VSPackage\-DLLs und andere Informationen in einem Windows Installer\-Paket \(. MSI\-Datei\) für die Bereitstellung für Ihre Kunden.  
  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ansichten und Adressen Hierarchien.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Bietet eine Übersicht über ein VSPackage, eine installierbare COM\-Objekt, das erweitert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung und beschreibt, wie Sie Ihre eigenen VSPackage implementieren.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Beschreibt, wie Sie Projekte verwenden, ändern Sie Code, kompilieren und Erstellen von Code und Code ausführen und Debuggen, und enthält Links zu ausführlichen Themen über das Erstellen von Projekttypen zur Verfügung.