---
title: Quellcode-Steuerelemente für die VSPackage-Design | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e10825bb9bc9659728fbaaeb023a595745b7bcd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642702"
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