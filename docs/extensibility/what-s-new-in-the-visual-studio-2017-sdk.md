---
title: Was&#39;Neues in Visual Studio 2017 SDK | Microsoft-Dokumentation
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 434a04aaa8389b4b09f32778d5de63bd2a7d687f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350793"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Was&#39;Neues in Visual Studio 2017 SDK

Visual Studio SDK hat die folgenden neuen und aktualisierten Funktionen für Visual Studio 2017.

## <a name="vsix-v3-format"></a>VSIX v3-format

Um die neue Lightweight-Installation von Visual Studio 2017 zu unterstützen, wurde die Erweiterung VSIX-Manifestformat auf Version 3 (VSIX v3) aktualisiert.

Das neue Format verfügt über Unterstützung für:

* Voraussetzungen für die erkannt und installiert, indem Sie die VSIX-Installationsprogramm werden explizit zu deklarieren.
* NGen-Assemblys, auf die Installation der Erweiterung.
* Installieren von Ressourcen außerhalb der üblichen erweiterungsstamm.

Zu diesen Änderungen finden Sie unter den folgenden Themen:

* [Änderungen an Erweiterbarkeit für Visual Studio 2017](breaking-changes-2017.md)
* [NGen-Unterstützung in VSIX v3](ngen-support.md)
* [Installieren Sie außerhalb des Ordners für Erweiterungen](set-install-root.md)
* [Häufig gestellte Fragen zu Visual Studio 2017-Erweiterbarkeit](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrieren Sie zu Visual Studio 2017-Erweiterungsprojekt

Aktualisieren Sie Ihre Erweiterungsprojekte und ihre VSIX-Manifeste auf Visual Studio 2017 finden Sie unter [Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Benutzerdefinierte Projekt- und Elementvorlagen

Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort der diese Vorlagen zu beschreiben. Sie können Visual Studio 2017 verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung, die mit MSI bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das manifest Vorlagenschema finden Sie unter [manifest Visual Studio-Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualisierte Erweiterung Leistungsrichtlinien

Es gibt eine neue [Vorgehensweise: Leistung der diagnoseerweiterung](how-to-diagnose-extension-performance.md) Artikel unter [verwalten VSPackages](managing-vspackages.md) um zu zeigen, wie Sie erkennen, und Analysieren der Auswirkungen der Erweiterung für Visual Studio starten und die Lösung Ladezeiten.
