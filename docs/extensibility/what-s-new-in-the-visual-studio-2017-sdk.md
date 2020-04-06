---
title: Was&#39;ist neu im Visual Studio 2017 SDK | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697198"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Neuer&#39;im Visual Studio 2017 SDK

Das Visual Studio SDK verfügt über die folgenden neuen und aktualisierten Features für Visual Studio 2017.

## <a name="vsix-v3-format"></a>VSIX v3-Format

Zur Unterstützung der neuen leichten Installation von Visual Studio 2017 wurde das VSIX-Erweiterungsmanifestformat auf Version 3 (VSIX v3) aktualisiert.

Das neue Format unterstützt:

* Explizites Deklarieren von Voraussetzungen, die vom VSIXInstaller erkannt und installiert werden sollen.
* Ngen-Baugruppen bei Erweiterungsinstallation.
* Installieren von Assets außerhalb des üblichen Erweiterungsstamms.

Weitere Informationen zu diesen Änderungen finden Sie in den folgenden Themen:

* [Änderungen an der Erweiterbarkeit für Visual Studio 2017](breaking-changes-2017.md)
* [NGen-Unterstützung in VSIX v3](ngen-support.md)
* [Installieren außerhalb des Ordners für Erweiterungen](set-install-root.md)
* [Häufig gestellte Fragen zur Erweiterbarkeit von Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrieren von Erweiterbarkeitsprojekt zu Visual Studio 2017

Informationen zum Aktualisieren Ihrer Erweiterbarkeitsprojekte und ihrer VSIX-Manifeste in Visual Studio 2017 finden Sie unter [Gewusst wie: Migrieren von Erweiterbarkeitsprojekten zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Benutzerdefinierte Projekt- und Elementvorlagen

Ab Visual Studio 2017 wird das Scannen nach benutzerdefinierten Projekt- und Elementvorlagen nicht mehr ausgeführt. Stattdessen muss die Erweiterung Vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort dieser Vorlagen beschreiben. Sie können Visual Studio 2017 verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie ihre Erweiterung mit einer MSI bereitstellen, müssen Sie die Vorlagenmanifestdateien von Hand generieren. Weitere Informationen finden Sie unter [Aktualisieren benutzerdefinierter Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das Vorlagenmanifestschema wird in [Visual Studio-Vorlagenmanifestschemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md)dokumentiert.

## <a name="updated-extension-performance-guidelines"></a>Aktualisierte Richtlinien für die Erweiterungsleistung

Es gibt einen neuen Artikel zur [Diagnose der Erweiterungsleistung](how-to-diagnose-extension-performance.md) unter [VsPackages verwalten,](managing-vspackages.md) um zu zeigen, wie die Auswirkungen der Erweiterung auf die Start- und Ladezeiten von Visual Studio erkannt und analysiert werden.
