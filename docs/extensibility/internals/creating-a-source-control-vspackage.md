---
title: "Erstellen eines VSPackages Datenquellen-Steuerelement | Microsoft Docs"
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
  - "Datenquellen-Steuerelement [Visual Studio SDK] Source Control-Pakete erstellen"
  - "Source Control-Pakete"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen eines VSPackages Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Dokumentation enthält Links zur Quellcodeverwaltung Architecture Overview eines pakets, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], welche API integriert ist, das über die implementiert werden müssen und Schnittstellen definierten von Diensten genutzt werden sollen, und ein Beispiel, in dem eine einfache Implementierung der Quellcodeverwaltung Paket veranschaulicht.  
  
 Bei einer Quellcodeverwaltung VSPackage können Sie einen tiefen Integrations Quellsteuerelement Pfad erstellen, damit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert.  Sie können das Paket, um die Benutzeroberfläche der Quellcodeverwaltung umgangen werden, die von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltung auf Anforderungen vom Projektsystem zu reagieren, und mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten wie **Projektmappen\-Explorer**interagieren gehostet wird.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bevollmächtigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Partner mit einem Mechanismus, um ein VSPackage erstellen, das mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit einem Dienst modells integriert werden kann.  
  
## In diesem Abschnitt  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Erläutert die Quellcodeverwaltung Paket, das eine erweiterte Quellcodeverwaltungs\-Plug\-In Alternative zum Implementieren von Funktionen für die Quellcodeverwaltung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ist.  
  
 [Architektur](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Legt ein Diagramm vor und erläutert die Komponenten eines pakets Quellcodeverwaltung.  
  
 [Features](../../extensibility/internals/source-control-vspackage-features.md)  
 Beschreibt die verschiedenen Features eines pakets Quellcodeverwaltung.  
  
 [Design\-Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Beschreibt die Struktur eines VSPackages das Paket für tiefe Integration der Quellcodeverwaltung implementieren muss.  
  
## Verwandte Abschnitte  
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert, wie ein Quellcodeverwaltungs\-Plug\-In diese Funktionen bereitstellt quellcodeverwaltungs in der Benutzeroberfläche der Quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erstellt.  
  
 [Quellcodeverwaltung](../../extensibility/internals/source-control.md)  
 Erläutert die Optionen zum Implementieren der Quellcodeverwaltung als integrierte Funktionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].