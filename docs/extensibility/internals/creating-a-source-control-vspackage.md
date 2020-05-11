---
title: Erstellen eines Quellcodeverwaltungs-VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709190"
---
# <a name="create-a-source-control-vspackage"></a>Erstellen eines Quellcodeverwaltungs-VSPackage
Diese Dokumentation enthält Links zur Architekturübersicht eines Quellcodeverwaltungspakets, das in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert ist, der API, die durch die zu implementierenden Schnittstellen und die zu nutzenden Dienste definiert wird, sowie ein Beispiel, das eine einfache Quellcodeverwaltungspaketimplementierung veranschaulicht.

 Mit einem Quellcodeverwaltungs-VSPackage können Sie einen tiefen Integrationspfad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]für die Quellcodeverwaltung erstellen, der in integriert werden soll. Es ermöglicht dem Paket, die standardmäßige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltungs-UI zu umgehen, die von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gehostet wird, auf Quellcodeverwaltungsanforderungen des Projektsystems zu reagieren und mit Komponenten wie **dem Projektmappen-Explorer**zu interagieren. Der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ermöglicht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Partnern einen Mechanismus zum Erstellen eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage, das in die Verwendung eines Dienstmodells integriert werden kann.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Erläutert das Quellcodeverwaltungspaket, das eine erweiterte Alternative zum Quellcodeverwaltungs-Plug-In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zum Implementieren von Quellcodeverwaltungsfeatures in darstellt.

- [Aufbau](../../extensibility/internals/source-control-vspackage-architecture.md)

 Stellt ein Diagramm vor und erläutert die Komponenten eines Quellcodeverwaltungspakets.

- [Features](../../extensibility/internals/source-control-vspackage-features.md)

 Beschreibt die verschiedenen Features eines Quellcodeverwaltungspakets.

- [Designelemente](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Beschreibt die Struktur des VSPackage, die ein Quellcodeverwaltungspaket für eine tiefe Integration implementieren muss.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Erläutert, wie ein Quellcodeverwaltungs-Plug-In erstellt wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Quellcodeverwaltungsfunktionen in der Quellcodeverwaltungsbenutzeroberfläche bereitstellt.

- [Quellcodeverwaltung](../../extensibility/internals/source-control.md)

 Erläutert die Optionen für die Implementierung der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltung als integriertes Feature von .
