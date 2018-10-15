---
title: Unterstützen mehrerer Versionen von Visual Studio | Microsoft-Dokumentation
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
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f68da8f7e397afef82c138af7d5228fe658dbb4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192606"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützen mehrerer Versionen von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Begriff *Seite-an-Seite* bedeutet, dass Sie installieren und mehrere Versionen eines Produkts auf dem gleichen Computer verwalten können. Für VSPackages bedeutet, dass an, dass ein Benutzer mehrere Versionen von Visual Studio auf demselben Computer installiert haben kann. Allerdings möglich keine Seite-an-Seite Ihre VSPackages Laden in eine einzelne Version von Visual Studio-Versionen.  
  
 Bevor Sie Ihr VSPackage in die Seite-an-Seite-Versionen von Visual Studio geladen werden können vornehmen, berücksichtigen Sie Folgendes:  
  
-   Sie müssen bestimmen, welche Seite-an-Seite Implementierungsstrategie für die Sie ausführen möchten.  
  
     Weitere Informationen finden Sie unter [auswählen zwischen freigegebenen "und" mit versionsverwaltung durch das VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Ihre Dateiformate Projektmappen- und Projektdateien müssen Ihre Strategie für die Implementierung passen.  
  
     Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md) und [Registrieren von Dateierweiterungen für Seite-an-Seite Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Das Installationsprogramm muss Ihre Strategie für die Implementierung behandeln, sodass mit versionsverwaltung durch das Komponenten sowie alle Versionen, gemeinsam genutzte Komponenten ordnungsgemäß installiert und registriert werden.  
  
     Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) sowie [Komponentenverwaltung](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installieren einer Version von Visual Studio auch eine entsprechende Version von installiert die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Installieren von Visual Studio 2010 und Visual Studio 2012 auf dem gleichen Computer z. B. auch Versionen 4.0 und 4.5 installiert die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]bzw.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Auswählen zwischen freigegebenen VSPackages und VSPackages mit Versionsangabe](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Erläutert, wie auf die Seite-an-Seite Probleme in Ihrem VSPackage zu beheben.  
  
 [Registrieren von Dateierweiterungen für parallele Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Beschreibt, wie Ihr VSPackage dateizuordnungen in einem Seite-an-Seite-Szenario registrieren kann.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Installieren von VSPackages](../misc/installing-vspackages.md)  
 Erläutert, wie VSPackages erstellt und installiert und wie Benutzer unterstützt werden, die mehrere Versionen von Visual Studio gleichzeitig ausführen.

