---
title: Informationen zu Dateierweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 680f9e9f79430ea53da3566686b058c44894e494
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776082"
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateierweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Registrieren einer Dateierweiterung aus einem VSPackage ordnen Sie es mit einer Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dies ist wichtig, wenn mehr als eine Version der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf einem Computer installiert ist.  
  
 Dateierweiterungen für VSPackages sind unter HKEY_CLASSES_ROOT Schlüssel mit einem Standardwert registriert, die auf den zugeordneten Programmbezeichner (ProgID) verweist.  
  
 Im folgenden finden ein Beispiel für die Registrierungsinformationen für die VCPROJ-Dateierweiterung:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Mit verknüpften Dateien [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] müssen mit versionsverwaltung durch das ProgID, z. B. `VisualStudio.vcproj.8.0`, um die Seite-an-Seite-Installationen des Produkts statusleisteneinstellungen zwischen Produktversionen verwalten können. Eine bestimmte Version ProgID auch können Sie standard-Verben wie öffnen, bearbeiten und so weiter, ohne überschreiben oder überschrieben wird, indem Sie andere Anwendungen oder Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 In bestimmten Fällen sollte die Programm-ID verknüpft ist, mit der Dateierweiterung nicht geändert werden. Z. B. die ProgID für die Erweiterung des htm-Datei (progid Htmlfile =) ist fest programmiert auf verschiedene Stellen in das Betriebssystem und ist allgemein bekannt und verwendet eine Verknüpfung mit htm- und HTML-Dateien.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Dateierweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Angeben von Dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

