---
title: Welche &#39; s in der Visual Studio-SDK 2017 | Microsoft Docs
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0be477d54ffeab52c415890c7d95447fa3f55ffc
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Welche &#39; s in der Visual Studio 2017 SDK

Das Visual Studio SDK hat die folgenden neuen und aktualisierten Features für Visual Studio-2017.

## <a name="vsix-v3-format"></a>VSIX-v3-format

Um die neue Lightweight-Installation von Visual Studio 2017 zu unterstützen, wurde das VSIX-Erweiterung manifest Format auf Version 3 (VSIX v3) aktualisiert.

Das neue Format wurde Unterstützung für:

* Deklarieren explizit Voraussetzungen erkannt und durch die VSIXInstaller installiert werden.
* Ngen'ing Assemblys, auf die Installation der Erweiterung.
* Installieren die Objekte außerhalb des üblichen Erweiterung Root.

Weitere Informationen zu diesen Änderungen finden Sie unter den folgenden Themen:

* [Änderungen an der Erweiterbarkeit für 2017](breaking-changes-2017.md)
* [NGen-Unterstützung in VSIX v3](ngen-support.md)
* [Installieren außerhalb des Ordners für Erweiterungen](set-install-root.md)
* [Häufig gestellte Fragen für die Erweiterbarkeit von Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrieren von auf 2017 von Visual Studio-Erweiterungsprojekt

Zum Aktualisieren der Erweiterbarkeit von Projekten und die VSIX-Manifest an Visual Studio 2017 finden Sie unter [Vorgehensweise: Migrieren Erweiterungsprojekte zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Benutzerdefinierte Projekt- und Elementvorlagen

Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort dieser Vorlagen zu beschreiben. Visual Studio-2017 können Sie um die VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio-2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Die Vorlage Manifestschema finden Sie im [Visual Studio Manifest Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualisierte Erweiterung Leistungsrichtlinien

Es gibt eine neue [wie: Diagnose Erweiterung Leistung](how-to-diagnose-extension-performance.md) Thema unter [Verwalten von VSPackages](managing-vspackages.md) um zu zeigen, wie Sie erkennen und Analysieren der Auswirkungen der Erweiterung für Visual Studio starten und die Lösung Ladezeiten.
