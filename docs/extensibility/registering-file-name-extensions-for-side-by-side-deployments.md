---
title: Registrieren von Dateierweiterungen für Seite-an-Seite-Bereitstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bdfb562ddfcce2584b8868c3c931c21f9dbc127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334231"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrieren von Dateierweiterungen für Seite-an-Seite-Bereitstellungen
Für VSPackages, die in einer Seite-an-Seite-Umgebung bereitgestellt werden, müssen Sie die Dateierweiterungen, um die richtige Version der Dateien zuzuordnen registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wenn Sie eine bestimmte Version Dateinamenerweiterung verwenden, wird nach der Registrierung können Benutzer öffnen Sie das Projekt und Element-Projektdateien in die entsprechende Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>In diesem Abschnitt
- [Informationen zu Dateierweiterungen](../extensibility/about-file-name-extensions.md) wird erläutert, wie die Dateinamenerweiterungen Weitere Erweiterungen registriert sind.

- [Angeben von dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md) enthält Informationen dazu, wie Sie Anwendungen, die geöffnet werden können, bearbeiten und usw., eine bestimmte Dateinamenerweiterung zu registrieren.

- [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md) wird erläutert, wie Verben zu registrieren.

- [Seite-an-Seite dateizuordnungen verwalten](../extensibility/managing-side-by-side-file-associations.md) beschreibt, wie Sie die Seite-an-Seite-Installationen, in dem Verarbeiten einer bestimmten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Öffnen einer Datei aufgerufen werden soll.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Unterstützen von mehreren Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) werden Probleme im Zusammenhang mit mehreren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und dem VSPackage während der Entwicklung und Bereitstellung für Endbenutzer.