---
title: Registrieren von Dateinamenerweiterungen für Side-By-Side-Bereitstellungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701541"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrieren von Dateinamenerweiterungen für side-by-side-Bereitstellungen
Für VSPackages, die in einer side-by-side-Umgebung bereitgestellt werden, müssen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Dateinamenerweiterungen registrieren, um die Dateien der richtigen Version von zuzuordnen. Sofern Sie keine versionsspezifische Dateinamenerweiterung verwenden, können Benutzer durch die Registrierung Ihre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Projekt- und Projektelementdateien in der entsprechenden Version von öffnen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Informationen zu Dateinamenerweiterungen](../extensibility/about-file-name-extensions.md) Erläutert, wie Dateinamenerweiterungen registriert werden.

- [Dateihandler für Dateinamenerweiterungen angeben](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Enthält Informationen zum Registrieren der Anwendungen, die eine bestimmte Dateinamenerweiterung öffnen, bearbeiten usw.

- [Register verbs für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md) Erläutert, wie Verben registriert werden.

- [Verwalten von seitenebenigen Dateizuordnungen](../extensibility/managing-side-by-side-file-associations.md) Erläutert, wie nebeneinander Installationen behandelt werden, bei [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denen eine bestimmte Version aufgerufen werden soll, um eine Datei zu öffnen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Unterstützung mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Beschreibt Probleme im Zusammenhang [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit mehreren Versionen und Ihrem VSPackage während der Entwicklung und Bereitstellung für Endbenutzer.
