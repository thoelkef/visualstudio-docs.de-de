---
title: Informationen zu Dateinamen Erweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148035"
---
# <a name="about-file-name-extensions"></a>Informationen zu Dateierweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine Dateierweiterung eines VSPackage registrieren, ordnen Sie es einer Version von zu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dies ist wichtig, wenn auf einem Computer mehr als eine Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installiert ist.  
  
 Dateierweiterungen für VSPackages werden unter HKEY_CLASSES_ROOT Schlüssel mit einem Standardwert registriert, der auf den zugeordneten programmatischen Bezeichner (ProgID) verweist.  
  
 Im folgenden finden Sie ein Beispiel für die Registrierungsinformationen für die Dateierweiterung. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Dateien [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die zugeordnet sind, müssen eine ProgID mit Versions Angabe aufweisen, wie z `VisualStudio.vcproj.8.0` . b., um parallele Installationen des Produkts zuzulassen, um Datei Erweiterungs Zuordnungen Zwischenprodukt Versionen beizubehalten. Eine versionsspezifische ProgID ermöglicht Ihnen außerdem die Verwendung von Standard Verben, wie z. b. öffnen, bearbeiten usw., ohne das Überschreiben oder Überschreiben durch andere Anwendungen oder Versionen von zu überschreiben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 In bestimmten Fällen sollte die mit einer Dateierweiterung verknüpfte ProgID nicht geändert werden. Beispielsweise ist die ProgID für die. htm-Dateierweiterung (ProgID = HTMLFILE) an mehreren Stellen im Betriebssystem hart codiert und in Verbindung mit. htm-und HTML-Dateien häufig bekannt und wird verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Registrieren von Dateinamen Erweiterungen für parallele bereit Stellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Angeben von Dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
