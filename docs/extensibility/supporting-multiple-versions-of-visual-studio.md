---
title: "Unterst&#252;tzung von mehreren Versionen von Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio unterstützt mehrere Versionen"
  - "VSPackages, Side-by-Side-Kompatibilität"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Unterst&#252;tzung von mehreren Versionen von Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Begriff *Side\-by\-Side* bedeutet, dass Sie installieren und mehrere Versionen eines Produkts auf demselben Computer verwalten können. VSPackages also, dass ein Benutzer mehrere Versionen von Visual Studio auf demselben Computer installiert sein kann. Allerdings haben nicht Side\-by\-Side\-Versionen Ihre VSPackages in eine einzige Version von Visual Studio geladen.  
  
 Vor der VSPackage in Side\-by\-Side\-Versionen von Visual Studio geladen werden können, beachten Sie Folgendes:  
  
-   Sie müssen bestimmen, welche Strategie für die Implementierung von Side\-by\-Side verfolgen möchten.  
  
     Weitere Informationen finden Sie unter [Auswählen zwischen freigegebenen und versioniert VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Die Projektmappen\- und Projektdateien Dateiformate müssen Ihre Strategie für die Implementierung passen.  
  
     Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md) und [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Das Installationsprogramm muss Ihre Strategie für die Implementierung behandeln, sodass mit Versionsangabe Komponenten sowie alle Versionen, gemeinsam genutzte Komponenten ordnungsgemäß installiert und registriert sind.  
  
     Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Verwaltung von Komponenten](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installation einer Version von Visual Studio eine entsprechende Version von installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Installieren von Visual Studio 2010 und Visual Studio 2012 auf demselben Computer z. B. auch Versionen 4.0 und 4.5 installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], bzw..  
  
## In diesem Abschnitt  
 [Auswählen zwischen freigegebenen und versioniert VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Erläutert, wie in Ihrer VSPackage Side\-by\-Side\-Problemen.  
  
 [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Beschreibt, wie das VSPackage dateizuordnungen in einem Seite\-an\-Seite\-Szenario registrieren kann.  
  
## Verwandte Abschnitte  
 [Installieren von VSPackages](../misc/installing-vspackages.md)  
 Erläutert das Erstellen und Installieren von VSPackages und Unterstützung von Benutzern, die gleichzeitig mehrere Versionen von Visual Studio ausgeführt werden.