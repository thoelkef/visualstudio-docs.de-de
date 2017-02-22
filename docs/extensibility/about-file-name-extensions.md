---
title: "Informationen zu Dateinamenerweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dateierweiterungen"
  - "Dateinamenerweiterungen"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Informationen zu Dateinamenerweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine Dateierweiterung aus einem VSPackage registrieren, ordnen Sie es mit einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dies ist wichtig, wenn mehr als eine Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf einem Computer installiert ist.  
  
 Dateierweiterungen für HKEY\_CLASSES\_ROOT\-Taste werden unter VSPackages mit einem Standardwert registriert, der dem zugeordneten Programmbezeichner \(ProgID\) zeigt.  
  
 Im Folgenden finden Sie ein Beispiel der Registrierungsinformationen für die VCPROJ\-Datei\-Erweiterung:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Die Dateien, die mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugeordnet werden, müssen ein Freigeben von ProgID, wie `VisualStudio.vcproj.8.0`verfügen, um parallelen Installationen des Produkts zu ermöglichen, den Dateierweiterung unter Produkt Versionen verwalten.  Ein versionsspezifisches ProgID können Sie auch standardmäßig verben verwenden, z. B. Bearbeiten öffnen usw. ohne den Aspekt des Überschreibens oder von anderen Anwendungen oder Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]überschrieben werden kann.  
  
 In bestimmten Fällen sollte der ProgID, der mit einer Dateierweiterung verknüpft ist, nicht geändert werden.  Beispielsweise ist die ProgID für die Dateierweiterung .htm\- \(ProgID\) \= htmlfile an mehreren Stellen im Betriebssystem hartcodiert wird und allgemein bekannt ist und in Verbindung mit .htm und .html\- Dateien verwendet.  
  
## Siehe auch  
 [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Angeben von Dateihandler für Dateinamenerweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)