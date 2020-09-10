---
title: Dateinamen Erweiterungen für Seite-an-Seite-IDES registrieren
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
ms.openlocfilehash: 68c343646055e6ce877d7bd15892ab1db0d0cbc5
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741698"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrieren von Dateinamen Erweiterungen für parallele bereit Stellungen
Für VSPackages, die in einer parallelen Umgebung bereitgestellt werden, müssen Sie Dateinamen Erweiterungen registrieren, um die Dateien der richtigen Version von zuzuordnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Die Registrierung ermöglicht es Benutzern, Ihre Projekt-und Projekt Element Dateien in der entsprechenden Version von zu öffnen, es sei denn, Sie verwenden eine versionsspezifische Dateinamenerweiterung [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>In diesem Abschnitt
- [Informationen zu Dateinamen Erweiterungen](../extensibility/about-file-name-extensions.md) Erläutert, wie Dateinamen Erweiterungen registriert werden.

- [Angeben von Datei Handlern für Dateinamen Erweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Enthält Informationen zum Registrieren der Anwendungen, die eine bestimmte Dateinamenerweiterung öffnen, bearbeiten usw.

- [Registrieren von Verben für Dateinamen Erweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md) Erläutert, wie Verben registriert werden.

- Parallele [Dateizuordnungen verwalten](../extensibility/managing-side-by-side-file-associations.md) Erläutert, wie parallele Installationen behandelt werden, bei denen eine bestimmte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden muss, um eine Datei zu öffnen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Unterstützung mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Beschreibt Probleme im Zusammenhang mit mehreren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und dem VSPackage während der Entwicklung und Bereitstellung für Endbenutzer.
