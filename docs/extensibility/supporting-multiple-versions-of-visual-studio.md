---
title: Unterstützung mehrerer Versionen von Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699475"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützen mehrerer Versionen von Visual Studio
Der Begriff *side-by-side* bedeutet, dass Sie mehrere Versionen eines Produkts auf demselben Computer installieren und verwalten können. Für VSPackages bedeutet dies, dass ein Benutzer mehrere Visual Studio-Versionen auf demselben Computer installiert haben kann. Es können Sie jedoch keine nebeneinander stehenden Versionen Ihrer VSPackages in eine einzelne Version von Visual Studio laden.

 Bevor Sie Ihr VSPackage in side-by-side-Versionen von Visual Studio laden können, sollten Sie Folgendes beachten:

- Sie müssen festlegen, welche Side-by-Side-Implementierungsstrategie Sie verfolgen möchten.

   Weitere Informationen finden Sie unter [Auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Ihre Projektmappen- und Projektdateiformate müssen zu Ihrer Implementierungsstrategie passen.

   Weitere Informationen finden Sie unter [Aktualisieren benutzerdefinierter Projekte](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) und [Registrieren von Dateinamenerweiterungen für Side-By-Side-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Ihr Installationsprogramm muss Ihre Implementierungsstrategie behandeln, damit versionierte Komponenten sowie Komponenten, die für alle Versionen freigegeben sind, ordnungsgemäß installiert und registriert werden.

   Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und auch [Komponentenverwaltung](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Durch die Installation einer Version von Visual Studio wird auch eine entsprechende Version von .NET Framework installiert. Wenn Sie beispielsweise Visual Studio 2010 und Visual Studio 2012 auf demselben Computer installieren, werden auch die Versionen 4.0 bzw. 4.5 von .NET Framework installiert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Erläutert, wie Sie Nebeneinander auftretende Probleme in Ihrem VSPackage beheben können.

- [Registrieren von Dateinamenerweiterungen für Side-By-Side-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Beschreibt, wie Ihr VSPackage Dateizuordnungen in einem nebeneinander-szenario registrieren kann.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
