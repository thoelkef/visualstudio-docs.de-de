---
title: Auswählen zwischen freigegebenen und versionierten VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739883"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Wählen Sie zwischen freigegebenen und versionierten VSPackages
Verschiedene Versionen von Visual Studio können auf demselben Computer nebeneinander bestehen. VSPackages kann jede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kombination von Versionen unterstützen.

 Sie können die nebeneinander stehende Installation von VSPackages über eine der beiden Strategien, die gemeinsame Strategie oder die versionierte Strategie, aktivieren. Beide berücksichtigen das Vorhandensein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mehrerer Versionen und zugehöriger Versionen von .NET Framework.

 In der freigegebenen Strategie ist ein VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]für die Verwendung in mehreren Versionen von registriert. In der versionierten Strategie werden mehrere VSPackage-DLLs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert, eine für jede Version, die Sie unterstützen.

## <a name="shared-vspackages"></a>Freigegebene VSPackages
 Die Verwendung eines freigegebenen VSPackage ist sinnvoll, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Sie dasselbe VSPackage in mehreren Versionen von verwenden. Um ein freigegebenes VSPackage zu implementieren, müssen Sie die folgenden Schritte ausführen:

- Machen Sie Ihr VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kompatibel mit mehreren Versionen von . Es gibt zwei Möglichkeiten, dies zu tun:

  - Beschränken Sie Ihr VSPackage auf die Verwendung [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nur der Funktionen der frühesten Version, die Sie unterstützen.

  - Programmieren Sie Ihr VSPackage, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um sich an die Version anzupassen, in der es ausgeführt wird. Wenn Abfragen für neuere Dienste fehlschlagen, kann Ihr VSPackage andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Dienste anbieten, die in älteren Versionen von unterstützt werden.

- Registrieren Sie Ihr VSPackage entsprechend. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md) und [Managed VSPackage-Registrierung](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Registrieren Sie Dateierweiterungen entsprechend. Weitere Informationen finden Sie unter [Registrieren von Dateinamenerweiterungen für nebeneinander vorgesehene Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Erstellen Sie ein Installationsprogramm, das Ihr [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage für die entsprechenden Versionen von bereitstellt. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Komponentenverwaltung](../extensibility/internals/component-management.md).

- Beheben Sie das Problem der Registrierungskollisionen. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md).

- Stellen Sie sicher, dass sowohl freigegebene als auch versionierte Dateien die Referenzzählung respektieren, um eine sichere Installation und Entfernung mehrerer Versionen zu ermöglichen. Weitere Informationen finden Sie unter [Komponentenverwaltung](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Versionierte VSPackages
 Unter der versionierten VSPackage-Strategie erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage für jede version, die Sie unterstützen. Dies ist angemessen, wenn Sie erwarten, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Vorteile der Dienste zu nutzen, die von späteren Versionen von bereitgestellt werden, da sich jedes VSPackage weiterentwickeln kann, ohne die anderen zu beeinträchtigen. Dennoch kann die versionierte Strategie, mehrere Binärdateien entweder aus einer einzelnen Codebasis oder aus mehreren unabhängigen Codebasen zu erstellen, eine größere Entwicklung als die gemeinsame Strategie mit sich bringen. Außerdem kann zusätzliche Einrichtungsarbeit erforderlich sein, da Sie entweder ein separates Setup für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jede Version oder ein einzelnes Setup erstellen müssen, das die installierten Versionen erkennt und die Ihr VSPackage unterstützt.

## <a name="binary-compatibility"></a>Binärkompatibilität
 Im Allgemeinen ermöglicht die Binärkompatibilität die Ausführung von VSPackages mit systemeigenem Code, der mit früheren Versionen von Visual Studio entwickelt wurde, in späteren Versionen von Visual Studio. Es gibt jedoch drei wichtige Ausnahmen:

- Wenn Ihr VSPackage auf einer bestimmten Version der Common Language Runtime [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] basiert, muss es bestimmen, in welcher Version es ausgeführt wird.

- Ein VSPackage kann von einem bestimmten Feature eines anderen VSPackage oder eines anderen Produkts abhängig sein. Folglich kann das VSPackage nur ausgeführt werden, wenn die Abhängigkeit erfüllt ist.

- Ein VSPackage kann von einem Sicherheitsupdate in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Service [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Pack oder einer späteren Version von betroffen sein. In diesen Fällen wird ein VSPackage, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] das mit einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] früheren Version des entwickelt wurde, möglicherweise nicht in Versionen von ausgeführt, nachdem das Sicherheitsupdate angewendet wurde. Sie können Ihr Paket jedoch mit der späteren Version neu erstellen und es auch in früheren Versionen ausführen lassen.

  Verwaltete VSPackages müssen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] einer [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Version von erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]werden und der, die mit der Zielversion von übereinstimmen.

  Neben der Planung der Binärkompatibilität für Ihre VSPackage-Binärdateien sollten Sie auch Lösungs- und Projektdateiformate berücksichtigen. Wenn Ihr VSPackage einen neuen Projekttyp erstellt, müssen Sie entscheiden, ob [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]es in nur einer Version oder in mehreren Versionen von ausgeführt werden kann. Weitere Informationen finden Sie unter [Aktualisieren benutzerdefinierter Projekte](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Komponentenmanagement](../extensibility/internals/component-management.md)
