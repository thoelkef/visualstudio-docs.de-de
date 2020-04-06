---
title: Erste Schritte mit Quellcodeverwaltungs-Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708345"
---
# <a name="get-started-with-source-control-plug-ins"></a>Erste Schritte mit Quellcodeverwaltungs-Plug-Ins
Um ein Quellcodeverwaltungs-Plug-In zu erstellen, müssen Sie eine DLL erstellen, die die in der Quellcodeverwaltungs-Plug-In-API definierten Funktionen implementiert, und dann die DLL mit registrieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um sie für die Verwendung in der Quellcodeversionssteuerung verfügbar zu machen.

 Für Quellcodeverwaltungs-Plug-Ins (Versionen 1.1, 1.2 und 1.3) stehen drei Versionen der Quellcodeverwaltungs-Plug-Ins zur Verfügung. Die hier dokumentierte Quellcodeverwaltungs-Plug-In-API ist Version 1.3. Es wurde entwickelt, um vollständig kompatibel mit Quellcodeverwaltung Plug-Ins unterstützen Versionen 1.1 und 1.2. Der Abschnitt Neuerungen im Abschnitt [Source Control Plug-in API Version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) enthält Details zu den neuen Funktionen, die in der neuesten Version der Quellcodeverwaltungs-Plug-In-API unterstützt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Beschreibt, wie die Registrierungseinträge erstellt werden, die zum Anschließen einer Quellcodeverwaltungs-DLL erforderlich sind.

- [Neuerungen in der Quellcodeverwaltungs-Plug-In-API Version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Bietet einen kurzen Überblick über die Änderungen, die an der Quellcodeverwaltungs-Plug-In-API in Version 1.3 vorgenommen wurden.

- [Neuerungen in der Quellcodeverwaltungs-Plug-In-API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Bietet einen kurzen Überblick über die Änderungen, die an der Quellcodeverwaltungs-Plug-In-API in Version 1.2 vorgenommen wurden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)

 Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-In-API bereit.

- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definiert das Quellcodeverwaltungs-Plug-In-SDK und beschreibt die enthaltenen Ressourcen.
