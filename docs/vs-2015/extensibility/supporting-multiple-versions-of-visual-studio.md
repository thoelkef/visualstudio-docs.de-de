---
title: Unterstützung mehrerer Versionen von Visual Studio 2015 | Microsoft-Dokumentation
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
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840837"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützen mehrerer Versionen von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Begriff *nebeneinander* bedeutet, dass Sie mehrere Versionen eines Produkts auf demselben Computer installieren und verwalten können. Für VSPackages bedeutet dies, dass ein Benutzer mehrere Visual Studio-Versionen auf demselben Computer installiert haben kann. Es ist jedoch nicht möglich, parallele Versionen ihrer VSPackages in eine einzelne Version von Visual Studio zu laden.

 Bevor Sie das VSPackage in parallele Versionen von Visual Studio laden können, berücksichtigen Sie Folgendes:

- Sie müssen bestimmen, welche parallele Implementierungsstrategie Sie befolgen möchten.

     Weitere Informationen finden Sie unter [auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Ihre Projektmappen-und Projektdatei Formate müssen ihrer Implementierungsstrategie entsprechen.

     Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md) und [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)parallele bereit Stellungen.

- Das Installationsprogramm muss Ihre Implementierungsstrategie verarbeiten, damit versionierte Komponenten und auch Komponenten, die von allen Versionen gemeinsam genutzt werden, ordnungsgemäß installiert und registriert werden.

     Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und auch der [Komponenten Verwaltung](../extensibility/internals/component-management.md).

    > [!NOTE]
    > Bei der Installation einer Version von Visual Studio wird auch eine entsprechende Version von installiert [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Wenn Sie z. b. Visual Studio 2010 und Visual Studio 2012 auf demselben Computer installieren, werden auch die Versionen 4,0 und 4,5 des installiert [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="in-this-section"></a>In diesem Abschnitt
 [Auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Erläutert, wie parallele Probleme in Ihrem VSPackage gelöst werden.

 [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) parallele bereit Stellungen Beschreibt, wie das VSPackage Dateizuordnungen in einem parallelen Szenario registrieren kann.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Installieren von VSPackages](../misc/installing-vspackages.md) Erläutert, wie VSPackages erstellt und installiert und wie Benutzer unterstützt werden, die mehrere Versionen von Visual Studio gleichzeitig ausführen.
