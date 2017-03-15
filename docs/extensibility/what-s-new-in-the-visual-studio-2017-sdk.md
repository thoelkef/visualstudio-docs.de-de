---
title: Neuigkeiten in Visual Studio SDK 2017 | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 60898d7cace1c10006436a8d98cbd7f7628cf972
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Was ist neu in Visual Studio 2017 SDK

>**Hinweis:** diese Dokumentation ist vorläufig und basierend auf der Visual Studio 2017 RC-Version.

Das Visual Studio SDK hat die folgenden neuen und aktualisierten Features für Visual Studio 2017.

## <a name="vsix-v3-format"></a>VSIX-v3-format

Zur Unterstützung der Installation des neuen leicht von Visual Studio 2017 wurde das VSIX-Erweiterung Manifeste-Format Version 3 (v3 VSIX) aktualisiert.

Das neue Format bietet Unterstützung für:

* Erforderliche Komponenten werden erkannt und installiert, indem Sie die VSIXInstaller deklarieren explizit.
* Ngen'ing Assemblys bei Installation der Erweiterung.
* Installieren von Ressourcen außerhalb des üblichen Erweiterung Root.

Weitere Informationen zu diesen Änderungen finden Sie unter den folgenden Themen:

* [Änderungen an Erweiterbarkeit für 2017](breaking-changes-2017.md)
* [Unterstützung von NGen in VSIX v3](ngen-support.md)
* [Installieren von außerhalb der Ordner "Extensions"](set-install-root.md)
* [Häufig gestellte Fragen für die Erweiterbarkeit von Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrieren zu Visual Studio 2017-Erweiterungsprojekt

Um weitere Informationen zum Aktualisieren Ihrer Erweiterungsprojekte und ihre VSIX-Manifeste auf Visual Studio 2017 finden Sie unter [wie: Erweiterungsprojekte migrieren, um Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Einfache Lösung laden (LSL)

Laden Sie einfache Lösung ist ein neues Feature in VS 2017, Ladezeit Lösung wird erheblich schneller produktiver ermöglicht. Wenn LSL aktiviert ist, wird Visual Studio nicht vollständig Projekte geladen, wenn Sie mit ihnen zu arbeiten beginnen.

LSL kann Visual Studio-Erweiterungen auswirken. Abhängen, deren Funktionen an einem Projekt vollständig geladenen Erweiterungen möglicherweise nicht funktioniert oder nicht ordnungsgemäß funktionieren. Finden Sie unter [Laden einer Projektmappe Lightweight](lightweight-solution-load-extension-impact.md) zur Feststellung, ob die Erweiterung wird möglicherweise beeinträchtigt werden, und erhalten einen Leitfaden zum Aktualisieren der Erweiterungs.

## <a name="custom-project-and-item-templates"></a>Benutzerdefinierte Projekt- und Elementvorlagen

Ab Visual Studio 2017 Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung Manifestdateien Vorlage bereitstellen, die den Installationsspeicherort dieser Vorlagen zu beschreiben. Visual Studio 2017 können Sie um die VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie die Vorlage Manifestdateien manuell erstellen. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Die Vorlage Manifestschema finden Sie unter [Visual Studio-Vorlage Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualisierte Erweiterung Leistungsrichtlinien

Es gibt eine neue [wie: Diagnose-Erweiterung Leistung](how-to-diagnose-extension-performance.md) Thema unter [Verwalten von VSPackages](managing-vspackages.md) um zu zeigen, wie Sie erkennen und Analysieren der Auswirkung der Erweiterung für Visual Studio starten und Lösung Ladezeiten.

