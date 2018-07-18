---
title: Unterstützung von mehreren Versionen von Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 317ec1f214d18989c3b2c5c27fe9df9309239631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137819"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützung von mehreren Versionen von Visual Studio
Der Begriff *Side-by-Side* bedeutet, dass Sie installieren und mehrere Versionen eines Produkts auf dem gleichen Computer verwalten können. Für VSPackages bedeutet, dass ein Benutzer mehrere Versionen von Visual Studio auf demselben Computer installiert haben kann. Allerdings können nicht Sie Seite-an-Seite-Versionen Ihre VSPackages, die in eine einzelne Version von Visual Studio geladen haben.  
  
 Bevor Sie Ihr VSPackage in Seite-an-Seite-Versionen von Visual Studio geladen werden kann vornehmen, berücksichtigen Sie Folgendes:  
  
-   Sie müssen bestimmen, welche Strategie für die Seite-an-Seite-Implementierung verfolgen möchten.  
  
     Weitere Informationen finden Sie unter [gemeinsam auswählen und mit Versionsangabe VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Die Dateiformate Projektmappen- und Projektdateien müssen Ihre Strategie für die Implementierung passen.  
  
     Weitere Informationen finden Sie unter [Upgrade benutzerdefinierte Projekte](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) und [registrieren Dateinamenerweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Das Installationsprogramm muss Ihre Strategie für die Implementierung behandeln, sodass mit Versionsangabe Komponenten sowie in allen Versionen gemeinsam genutzte Komponenten ordnungsgemäß installiert und registriert sind.  
  
     Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) sowie [Komponente Management](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installation einer Version von Visual Studio auch eine entsprechende Version von installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Installieren von Visual Studio 2010 und Visual Studio 2012 auf demselben Computer z. B. auch Versionen 4.0 und 4.5 installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]bzw.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Auswählen zwischen freigegebenen VSPackages und VSPackages mit Versionsangabe](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Erläutert die Seite-an-Seite-Probleme in Ihrem VSPackage zu beheben.  
  
 [Registrieren von Dateierweiterungen für parallele Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Beschreibt, wie Ihr VSPackage dateizuordnungen in einem Seite-an-Seite-Szenario registrieren kann.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
