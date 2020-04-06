---
title: Erstellen eines Quellcodeverwaltungs-Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709173"
---
# <a name="create-a-source-control-plug-in"></a>Erstellen eines Quellcodeverwaltungs-Plug-Ins
Das Visual Studio SDK stellt Ressourcen bereit, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denen Sie der integrierten Entwicklungsumgebung (IDE) Quellcodeverwaltungsfunktionen hinzufügen können. Sie können jede Plug-In-DLL verwenden, die der in dieser Dokumentation beschriebenen Quellcodeverwaltungs-Plug-In-API entspricht.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Beschreibt die Installation eines Quellcodeverwaltungs-Plug-Ins und hebt die derzeit verfügbaren Quellsteuerungs-Plug-In-API-Versionen hervor.

- [Aufbau](../../extensibility/internals/source-control-plug-in-architecture.md)

 Verwendet ein Architekturdiagramm, um die Integration eines Quellcodeverwaltungs-Plug-Ins mit der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE zu erklären.

- [Testanleitung](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Enthält Anleitungen zum Testen der Installation und des Betriebs eines Quellcodeverwaltungs-Plug-Ins.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert, wie ein Quellcodeverwaltungs-VSPackage erstellt wird, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht nur Quellcodeverwaltungsfunktionen bereitstellt, sondern auch die Quellcodeverwaltungsbenutzeroberfläche ersetzt.

- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)

 Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-In-API bereit.

- [Quellcodeverwaltung](../../extensibility/internals/source-control.md)

 Erläutert die Optionen für die Implementierung der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltung als integriertes Feature von .
