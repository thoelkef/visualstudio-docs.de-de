---
title: Verwaltung von Komponenten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ef2edb8996984f943ce3d7ec168eed0692f2493
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110075"
---
# <a name="component-management"></a>Verwaltung von Komponenten
Einheiten von Aufgaben in der Windows Installer werden als Windows Installer-Komponenten (manchmal als WICs oder nur Komponenten bezeichnet) bezeichnet. Eine GUID identifiziert jedes WIC, wird die grundlegende Einheit der Installation und die verweiszählung für Einrichtungen, die Windows Installer verwenden.

 Obwohl Sie mehrere Produkte verwenden können, um Ihre VSPackage-Installationsprogramm zu erstellen, diese Diskussion wird von der Verwendung von Windows Installer (*MSI*) Dateien. Wenn Sie das Installationsprogramm zu erstellen, müssen Sie die Bereitstellung, damit die richtige verweiszählung jederzeit geschieht ordnungsgemäß verwalten. Daher verschiedene Versionen des Produkts nicht beeinträchtigen oder Unterbrechung der jeweils anderen eine Mischung aus installieren und Deinstallieren von Szenarien.

 Windows Installer tritt auf, der auf der Komponentenebene verweiszählung. Sie müssen sorgfältig Organisieren Ihrer Ressourcen – Dateien, Registrierungseinträge und So weiter – in Komponenten. Es gibt andere Ebenen der Organisation, z. B. Module, Funktionen und -Produkte –, mit denen in verschiedenen Szenarien. Weitere Informationen finden Sie unter [Windows Installer-Grundlagen](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Richtlinien der Erstellung von Setup für Seite-an-Seite-installation

- Author-Dateien und Registrierungsschlüssel, die für die Versionen, die in ihren eigenen Komponenten freigegeben werden.

     Auf diese Weise können Sie ganz einfach auf die nächste Version zu verwenden. Z. B. Dateierweiterungen für Typbibliotheken, die global registriert sind, andere Elemente im registriert **HKEY_CLASSES_ROOT**und so weiter.

- Gruppieren Sie gemeinsam genutzte Komponenten werden in separaten Mergemodule.

     Diese Strategie hilft dabei, Autor ordnungsgemäß für die Seite-an-Seite-Installation, die für die Zukunft.

- Installieren Sie die freigegebenen Dateien und Registrierungsschlüsseln mithilfe der gleichen Windows Installer-Komponenten über Versionen hinweg.

     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn eine mit versionsverwaltung durch das VSPackage wird deinstalliert, aber einem anderen VSPackage ist weiterhin installiert werden.

- Mischen Sie versioniert und freigegebene Elemente in der gleichen Komponente nicht.

     Auf diese Weise macht es unmöglich, freigegebene Elemente zu einem globalen Speicherort und Versionselementen, isolierte Standorte zu installieren.

- Haben Sie keine freigegebenen Registrierungsschlüssel, die auf Dateien Versionsnummern verweisen.

     Wenn Sie dies tun, werden bei der Installation von einem anderen mit versionsverwaltung durch das VSPackage die gemeinsam verwendeten Schlüssel überschrieben. Wenn Sie die zweite Version entfernen, ist die Datei, die auf der der Schlüssel verweist nicht mehr vorhanden.

## <a name="see-also"></a>Siehe auch
- [Wählen Sie zwischen freigegebenen und mit versionsverwaltung durch das VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage-setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)