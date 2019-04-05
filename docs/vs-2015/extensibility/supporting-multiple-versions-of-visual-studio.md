---
title: Unterstützen mehrerer Versionen von Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a4ad8b128ea614ba60a19c3526d20af80aab937
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959701"
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
 [Auswählen zwischen freigegebenen "und" mit versionsverwaltung durch das VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) wird erläutert, wie Seite-an-Seite Probleme in Ihrem VSPackage zu beheben.

 [Registrieren von Dateierweiterungen für Seite-an-Seite Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) wird beschrieben, wie Ihr VSPackage dateizuordnungen in einem Seite-an-Seite-Szenario registrieren kann.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Installieren von VSPackages](../misc/installing-vspackages.md) wird erläutert, wie VSPackages erstellt und installiert und Benutzer unterstützen, die mehrere Versionen von Visual Studio zur gleichen Zeit ausgeführt werden.
