---
title: Quellcodeverwaltung VSPackage Designelemente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705009"
---
# <a name="source-control-vspackage-design-elements"></a>Entwurfselemente von Quellcodeverwaltungs-VSPackages
Die Themen in diesem Abschnitt beschreiben die Struktur, die das Quellcodeverwaltungspaket VSPackage für eine tiefe Integration implementieren muss. Außerdem werden die Schnittstellen und Dienste aufgeführt, die das Quellcodeverwaltungssteuerelement VSPackage implementieren kann, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Schnittstellen und Dienste, die das Quellcodeverwaltungspaket von anderen Komponenten verwenden kann, um sein Quellcodeverwaltungsmodell und seine Funktionalität zu unterstützen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [VSPackage-Struktur](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiert die Struktur der Quellcodeverwaltung VSPackage.

- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Listet paketbezogene Schnittstellen und Dienste für die Quellcodeverwaltung auf.

- [Bereitgestellte Dienste](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Beschreibt den Quellcodeverwaltungsdienst, der von der Quellcodeverwaltung VSPackage bereitgestellt wird.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert, wie ein Quellcodeverwaltungs-VSPackage erstellt wird, das nicht nur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungsfunktionen bereitstellt, sondern auch zum Anpassen der Quellcodeverwaltungsbenutzeroberfläche verwendet werden kann.
