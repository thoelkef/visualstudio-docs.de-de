---
title: Informationen zu Dateierweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fd181bb7daca21ff263dcb7989a0aecbef3ed278
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081695"
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateierweiterungen
Beim Registrieren einer Dateierweiterung aus einem VSPackage ordnen Sie es mit einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dies ist wichtig, wenn mehr als eine Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf einem Computer installiert ist.  
  
 Dateierweiterungen für VSPackages registriert sind, klicken Sie unter **HKEY_CLASSES_ROOT** Schlüssel mit einem Standardwert, der auf den zugeordneten Programmbezeichner (ProgID) verweist.  
  
 Das folgende Beispiel zeigt Informationen zur Registrierung der *.vcproj* Dateierweiterung:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Mit verknüpften Dateien [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] müssen mit versionsverwaltung durch das ProgID, z. B. `VisualStudio.vcproj.8.0`. Eine ProgID mit Versionsangabe ermöglicht Seite-an-Seite-Installationen des Produkts zu Zuordnungen zwischen Produktversionen von Dateierweiterungen zu verwalten. Eine bestimmte Version ProgID auch können Sie standard-Verben wie öffnen, bearbeiten und so weiter, ohne überschreiben oder überschrieben wird, indem Sie andere Anwendungen oder Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In bestimmten Fällen sollte die Programm-ID verknüpft ist, mit der Dateierweiterung nicht geändert werden. Z. B. die ProgID für die *.htm* Dateierweiterung (progid Htmlfile =) in eine Anzahl von Stellen in das Betriebssystem ist hartcodiert und ist allgemein bekannt und verwendet eine Verknüpfung mit *.htm* und *.html* Dateien.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Dateierweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Angeben von dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)