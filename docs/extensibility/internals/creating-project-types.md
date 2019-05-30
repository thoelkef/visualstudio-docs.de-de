---
title: Erstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 005765cb66a23f2efcf0c8defb323120d79bef60
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314564"
---
# <a name="create-project-types"></a>Erstellen von Projekttypen
Sie können die erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch einen neuen Projekttyp erstellen. Um einen neuen Projekttyp zu erstellen, müssen Sie einige Konzepte verstehen und eine Reihe von Schritten ausführen. Die folgenden Themen enthalten eine Übersicht über zum Erstellen von Projekttypen zur Verfügung.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md)

 Beschreibt, Element, Projekt-Datei-Persistenz und Engagement Mechanic entwurfsentscheidungen, die Sie vornehmen, bevor ein neuer Projekttyp erstellen.

- [Prüfliste: Erstellen Sie neue Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)

 Bietet eine Übersicht über die Schritte, die Sie befolgen müssen, um einen neuen Projekttyp zu erstellen, der Programmierung Aufgaben wie das Bearbeiten von Code und kompilieren, erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.

- [Erstellen von Projektinstanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Enthält Informationen zum Bereitstellen und verwenden zum Erstellen von Instanzen eines neuen Projekts eine Projektzuordnungsinstanz.

- [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)

 Enthält Codebeispiele, die von Anweisungen aus der Registrierung, die Standardpfade und Daten und eine Tabelle bereitstellen, die Einträge aus dem Registrierungsskript "for each-Anweisung enthalten.

- [Projektpersistenz](../../extensibility/internals/project-persistence.md)

 Erläutert die Verwendung von `IPersistFileFormat` Datei- und nicht-Datei-basiertes Projektobjekte beibehalten werden.

- [Verwenden von MSBuild](../../extensibility/internals/using-msbuild.md)

 Beschreibt, wie Ihr Projekttyp die [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] -build-Engine, um Benutzern das Erstellen von ermöglichen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und in der Befehlszeile.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Unterstützung von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Erläutert die Architektur des Code-Tools wie z. B. Anzeigen der **Objektkatalog** und **Klassenansicht** Fenster. Beschreibt die Schnittstellen und Methoden, mit dem Objektkatalog in ein VSPackage implementiert werden.

- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Erläutert die Bedeutung von Projekten bei der bestimmen, welcher Editor verwendet wird, wenn ein Projektelement geöffnet wird und wie die Ressourcen des Projekts geändert werden können.

- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Zeigt, wie Ihr VSPackage über eine eigene eindeutige Identität gewähren und wie die VSPackage-DLLs und andere Informationen in einer Windows Installer-Paket zu umschließen ( *. MSI* Datei) für die Bereitstellung für Ihre Kunden.

- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ansichten und Adressen Hierarchien.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Bietet einen Überblick über die ein VSPackage, ein installierbares COM-Objekt, das erweitert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung und erläutert, wie Sie eigene VSPackages zu implementieren.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert, wie Projekte, Code zu ändern, kompilieren und erstellen Sie Code, und Code ausführen und Debuggen, und enthält Links zu ausführlichen Themen zur Vorgehensweise: Erstellen von Projekttypen zur Verfügung.