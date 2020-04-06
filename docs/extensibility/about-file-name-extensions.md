---
title: Informationen zu Dateinamenerweiterungen | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740344"
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateinamenerweiterungen
Wenn Sie eine Dateierweiterung eines VSPackage registrieren, ordnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Sie sie einer Version von zu. Dies ist wichtig, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mehr als eine Version von auf einem Computer installiert ist.

 Dateierweiterungen für VSPackages werden unter **HKEY_CLASSES_ROOT** Schlüssel mit einem Standardwert registriert, der auf den zugeordneten programmatischen Bezeichner (ProgID) verweist.

 Das folgende Beispiel zeigt Registrierungsinformationen für die *Dateierweiterung .vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Dateien, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die einer versionierten ProgID `VisualStudio.vcproj.8.0`zugeordnet sind, z. B. . Eine versionierte ProgID ermöglicht die nebeneinander liegenden Installation des Produkts, um Dateierweiterungszuordnungen zwischen Produktversionen beizubehalten. Mit einer versionsspezifischen ProgID können Sie auch Standardverben wie Öffnen, Bearbeiten usw. verwenden, ohne dass sie von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]anderen Anwendungen oder Versionen von überschrieben werden müssen.

 In bestimmten Fällen sollte die ProgID, die einer Dateierweiterung zugeordnet ist, nicht geändert werden. Beispielsweise ist die ProgID für die *.htm-Dateierweiterung* (progid = htmlfile) an mehreren Stellen im Betriebssystem hartcodiert und weithin bekannt und wird in Verbindung mit *.htm-* und *HTML-Dateien* verwendet.

## <a name="see-also"></a>Weitere Informationen
- [Registrieren von Dateinamenerweiterungen für side-by-side-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dateihandler für Dateinamenerweiterungen angeben](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
