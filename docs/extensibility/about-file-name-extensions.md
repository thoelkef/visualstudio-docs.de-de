---
title: Informationen zu Dateinamenerweiterungen | Microsoft Docs
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
ms.openlocfilehash: 2c940319cd0ce3204f6dd9bb62e731de49b8baac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108468"
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