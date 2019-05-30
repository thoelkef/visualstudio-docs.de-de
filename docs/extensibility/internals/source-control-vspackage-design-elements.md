---
title: Quellcode-Steuerelemente für die VSPackage-Design | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e9b22ea32698d6e996bfee618b0b5ca4da5943d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322483"
---
# <a name="source-control-vspackage-design-elements"></a>Entwurfselemente von Quellcodeverwaltungs-VSPackages
Die Themen in diesem Abschnitt beschreiben die Struktur der quellcodeverwaltung, die VSPackages, für die Tiefe Integration implementieren muss. Zudem werden die Schnittstellen aufgelistet und können Dienste, die Quelle VSPackage steuern, implementieren und die Schnittstellen und Dienste können von anderen das Quellcodeverwaltungs-VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten zur Unterstützung ihrer Quelle zu steuern, Modell und Funktionen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [VSPackage-Struktur](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiert die Struktur des Datenquellen-Steuerelements VSPackage.

- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Liste von Steuerelement paketbezogene Quellschnittstellen und Diensten.

- [Bereitgestellte Dienste](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Beschreibt den quellcodeverwaltungsdienst von das Quellcodeverwaltungs-VSPackage bereitgestellt.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert, wie ein Quellcodeverwaltungs-VSPackage zu erstellen, die nicht nur Quellcodeverwaltungsfunktionen bereitstellt, sondern dienen zum Anpassen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Datenquellen-Steuerelement-Benutzeroberfläche.