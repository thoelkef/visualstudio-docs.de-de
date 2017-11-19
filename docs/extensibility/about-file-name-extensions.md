---
title: Informationen zu Dateinamenerweiterungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aba03fd68fc5e0e68dbf13887de0c25094fa951
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateinamenerweiterungen
Beim Registrieren einer Erweiterungs von einem VSPackage, ordnen Sie dieses einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dies ist wichtig, wenn mehr als eine Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf einem Computer installiert ist.  
  
 Dateierweiterungen für VSPackages sind unter HKEY_CLASSES_ROOT Schlüssel hat den Standardwert registriert, die auf die zugeordneten Programmbezeichner (ProgID) verweist.  
  
 Im folgenden finden ein Beispiel für die Registrierungsinformationen für die Dateierweiterung VCPROJ:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Zugeordneten Dateien [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] benötigen mit Versionsangabe ProgID, z. B. `VisualStudio.vcproj.8.0`, um die Seite-an-Seite-Installationen des Produkts Datei Erweiterung Zuordnungen zwischen Produktversionen verwalten können. Eine versionsspezifische ProgID ermöglicht auch die Standardverben, z. B. öffnen, bearbeiten und usw. ohne überschreiben oder überschrieben wird, indem Sie andere Anwendungen oder-Versionen verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In bestimmten Fällen sollte die ProgID verknüpft sind, mit der Erweiterung nicht geändert werden. Angenommen, die ProgID für die Erweiterung der htm-Datei (progid = Htmlfile) ist schwer in einer Reihe stellen im Betriebssystem codiert und ist allgemein bekannt und verwendet eine Zuordnung mit htm- und HTML-Dateien.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren Dateierweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Angeben von Dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)