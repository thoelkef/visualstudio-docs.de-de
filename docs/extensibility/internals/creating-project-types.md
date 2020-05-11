---
title: Erstellen von Projekttypen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709070"
---
# <a name="create-project-types"></a>Erstellen von Projekttypen
Sie können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erweitern, indem Sie einen neuen Projekttyp erstellen. Um einen neuen Projekttyp zu erstellen, müssen Sie mehrere Konzepte verstehen und eine Reihe von Schritten ausführen. Die folgenden Themen geben einen Überblick über das Erstellen von Projekttypen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Projekttypentwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md)

 Erläutert die Entscheidungen über das Element, die Persistenz von Projektdateien und die Konstruktionsentscheidungen für die Verpflichtungsmechanik, die Sie treffen müssen, bevor Sie einen neuen Projekttyp erstellen.

- [Checkliste: Neue Projekttypen erstellen](../../extensibility/internals/checklist-creating-new-project-types.md)

 Bietet einen Überblick über die Schritte, die Sie ausführen müssen, um einen neuen Projekttyp zu erstellen, der Programmieraufgaben wie das Bearbeiten von Code und das Kompilieren, Erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.

- [Erstellen von Projektinstanzen mithilfe von Projektfabriken](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Enthält Informationen zum Bereitstellen und Verwenden einer Projektfactory zum Erstellen von Instanzen eines neuen Projekts.

- [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)

 Stellt Codebeispiele von Anweisungen aus der Registrierung bereit, die Standardpfade und -daten bereitstellen, sowie eine Tabelle, die Einträge aus dem Registrierungsskript für jede Anweisung enthält.

- [Projektpersistenz](../../extensibility/internals/project-persistence.md)

 Erläutert die Verwendung `IPersistFileFormat` von Datei- und nicht dateibasierten Projektobjekten.

- [MSBuild verwenden](../../extensibility/internals/using-msbuild.md)

 Beschreibt, wie Ihr Projekttyp das [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] Buildmodul [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden kann, damit Benutzer aus und in der Befehlszeile erstellen können.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Unterstützung von Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Erläutert die Architektur von Codeanzeigetools wie dem **Fenster Objektbrowser** und **Klassenansicht.** Beschreibt die Schnittstellen und Methoden, die zum Implementieren des Objektbrowsings in einem VSPackage verwendet werden.

- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Erläutert die Bedeutung, die Projekte bei der Bestimmung des Editors beim Öffnen eines Projektelements spielen und wie Projektressourcen bearbeitet werden können.

- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Zeigt, wie Sie Ihrem VSPackage eine eigene eindeutige Identität verleihen und wie Sie Ihre VSPackage-DLLs und andere Informationen in einem Windows Installer-Paket ( umschließen.* MSI-Datei)* für die Bereitstellung an Ihre Kunden.

- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Beschreibt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wie Hierarchien angezeigt und adressiert werden.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Bietet einen Überblick über ein VSPackage, ein installierbares COM-Objekt, das die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung erweitert und erläutert, wie Sie Ihr eigenes VSPackage implementieren.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert die Verwendung von Projekten zum Ändern von Code, Kompilieren und Erstellen von Code sowie Ausführen und Debuggen von Code und enthält Links zu detaillierten Themen zum Erstellen von Projekttypen.
