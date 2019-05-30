---
title: Erstellen eines Quellcodeverwaltungs-VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259273eee51c74eb7cb5ca4534db9bc575fd1758
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345491"
---
# <a name="create-a-source-control-vspackage"></a>Erstellen eines Quellcodeverwaltungs-VSPackage
Diese Dokumentation enthält Links zu der Architekturübersicht des ein Source-Control-Paket integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die API, die durch die Schnittstellen implementiert werden und die Dienste zur Nutzung definiert wird, und ein Beispiel, das veranschaulicht, eine einfache Quelle Steuern Sie die paketimplementierung.

 Sie können mit der quellcodeverwaltung VSPackage, einen enge Integration Pfad für die quellcodeverwaltung für die Integration erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dadurch werden das Paket, das Standard-Datenquellen-Steuerelement von gehosteten UI umgehen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], reagieren auf Source-Control-Anforderungen aus dem Projektsystem und interagieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten wie z. B. **Projektmappen-Explorer**. Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen Mechanismus für die ein VSPackage zu erstellen, die integriert werden können Partner [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe eines Dienstmodells.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Erläutert das Quellcodeverwaltungspaket, die eine erweiterte Alternative zum das Quellcodeverwaltungs-Plug-In für die Implementierung von Funktionen in quellcodeverwaltung ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Architektur](../../extensibility/internals/source-control-vspackage-architecture.md)

 Zeigt ein Diagramm und erläutert die Komponenten ein Quellcode-Verwaltungspaket.

- [Features](../../extensibility/internals/source-control-vspackage-features.md)

 Beschreibt die verschiedenen Funktionen ein Quellcode-Verwaltungspaket.

- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Beschreibt die Struktur des VSPackage, die ein Quellcode-Verwaltungspaket für die Tiefe Integration implementieren müssen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, die Quellcodeverwaltungsfunktionen in stellt das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Source Control-Benutzeroberfläche (UI).

- [Datenquellen-Steuerelement](../../extensibility/internals/source-control.md)

 Erläutert die Optionen zum Implementieren von Datenquellen-Steuerelement als eine integrierte Funktion von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
