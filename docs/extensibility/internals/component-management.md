---
title: Komponentenverwaltung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709334"
---
# <a name="component-management"></a>Komponentenmanagement
Aufgabeneinheiten im Windows Installer werden als Windows Installer-Komponenten bezeichnet (manchmal auch als WICs oder nur als Komponenten bezeichnet). Eine GUID identifiziert jedes WIC, die grundlegende Einheit der Installation und Referenzzählung für Setups, die Windows Installer verwenden.

 Obwohl Sie mehrere Produkte verwenden können, um Ihr VSPackage-Installationsprogramm zu erstellen, setzt diese Diskussion die Verwendung von Windows Installer -*.msi*) Dateien voraus. Beim Erstellen des Installationsprogramms müssen Sie die Dateibereitstellung ordnungsgemäß verwalten, sodass die korrekte Verweiszählung jederzeit erfolgt. Folglich werden verschiedene Versionen Ihres Produkts sich in einer Mischung aus Installations- und Deinstallationsszenarien nicht gegenseitig stören oder brechen.

 In Windows Installer erfolgt die Verweiszählung auf Komponentenebene. Sie müssen Ihre Ressourcen – Dateien, Registrierungseinträge usw. – sorgfältig in Komponenten organisieren. Es gibt andere Organisationsebenen, z. B. Module, Features und Produkte, die in verschiedenen Szenarien hilfreich sein können. Weitere Informationen finden Sie unter [Windows Installer-Grundlagen](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Richtlinien für die Erstellung von Erstellungseinstellungen für die nebeneinander-installation

- Erstellen Sie Dateien und Registrierungsschlüssel, die von Versionen in ihren eigenen Komponenten gemeinsam verwendet werden.

     Auf diese Weise können Sie sie in der nächsten Version einfach nutzen. Geben Sie beispielsweise Bibliotheken ein, die global registriert sind, Dateierweiterungen, andere Elemente, die in **HKEY_CLASSES_ROOT**registriert sind usw.

- Gruppieren Sie gemeinsam genutzte Komponenten in separate Mergemodule.

     Diese Strategie hilft Ihnen, die erstellung sie korrekt für die nebeneinander gerichtete Installation zu erstellen.

- Installieren Sie freigegebene Dateien und Registrierungsschlüssel, indem Sie die gleichen Windows Installer-Komponenten versionenübergreifend verwenden.

     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn ein versioniertes VSPackage deinstalliert wird, aber ein anderes VSPackage noch installiert ist.

- Mischen Sie keine versionierten und freigegebenen Elemente in derselben Komponente.

     Dies macht es unmöglich, freigegebene Elemente an einem globalen Speicherort und versionierte Elemente an isolierten Speicherorten zu installieren.

- Sie verfügen nicht über freigegebene Registrierungsschlüssel, die auf versionierte Dateien verweisen.

     Wenn Sie dies tun, werden die freigegebenen Schlüssel überschrieben, wenn ein anderes versioniertes VSPackage installiert wird. Nachdem Sie die zweite Version entfernt haben, ist die Datei, auf die der Schlüssel zeigt, verschwunden.

## <a name="see-also"></a>Weitere Informationen
- [Wählen Sie zwischen freigegebenen und versionierten VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage-Setup-Szenarien](../../extensibility/internals/vspackage-setup-scenarios.md)
