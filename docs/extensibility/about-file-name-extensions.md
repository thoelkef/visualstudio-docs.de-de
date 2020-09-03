---
title: Informationen zu Dateinamen Erweiterungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740344"
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateinamen Erweiterungen
Wenn Sie eine Dateierweiterung eines VSPackage registrieren, ordnen Sie es einer Version von zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Dies ist wichtig, wenn auf einem Computer mehr als eine Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert ist.

 Dateierweiterungen für VSPackages werden unter **HKEY_CLASSES_ROOT** Schlüssel mit einem Standardwert registriert, der auf den zugeordneten programmatischen Bezeichner (ProgID) verweist.

 Das folgende Beispiel zeigt Registrierungsinformationen für die Dateierweiterung *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Dateien [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die zugeordnet sind, müssen eine ProgID mit Versions Angabe aufweisen, z `VisualStudio.vcproj.8.0` . b.. Eine versionierte ProgID ermöglicht parallele Installationen des Produkts, um Datei Erweiterungs Zuordnungen Zwischenprodukt Versionen beizubehalten. Eine versionsspezifische ProgID ermöglicht Ihnen außerdem die Verwendung von Standard Verben, wie z. b. öffnen, bearbeiten usw., ohne das Überschreiben oder Überschreiben durch andere Anwendungen oder Versionen von zu überschreiben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 In bestimmten Fällen sollte die mit einer Dateierweiterung verknüpfte ProgID nicht geändert werden. Beispielsweise ist die ProgID für die *. htm* -Dateierweiterung (ProgID = HTMLFILE) an mehreren Stellen im Betriebssystem hart codiert und in der Zuordnung zu *htm* -und *HTML* -Dateien allgemein bekannt.

## <a name="see-also"></a>Weitere Informationen
- [Registrieren von Dateinamen Erweiterungen für parallele bereit Stellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Angeben von Datei Handlern für Dateinamen Erweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
