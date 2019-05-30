---
title: Architektur von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318898"
---
# <a name="project-types-architecture"></a>Architektur von Projekttypen
Dieser Abschnitt enthält ausführliche Informationen zur Architektur von Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>In diesem Abschnitt
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)

 Listet die Dienste, die ein Projekttyp nutzen kann und die Schnittstellen, die sie implementieren muss.

- [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)

 Beschreibt die Schnittstellen Projekttypen müssen implementieren und optional implementieren können, um zusätzliche Funktionen bereitzustellen.

- [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)

 Geben Sie die erleichtert Ihnen die Entscheidung, wenn Sie ein Projekt erstellen müssen und Sie können beim Verwenden einer anderen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Erweiterbarkeitsfunktion wie VSPackages und Editoren, um das gleiche Ziel zu erreichen.

- [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)

 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hierarchien und Auswahlkontext verwendet, um eine konsistente und vereinfachte Benutzeroberfläche bereitzustellen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)

 Erläutert, wie Sie das Verhalten der Projektsysteme von Anpassen von Projektuntertypen ermöglichen [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Projekttypen](../../extensibility/internals/project-types.md)

 Bietet eine Übersicht über Projekte als die grundlegenden Bausteine von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Links werden zu weiteren Themen bereitgestellt, die erläutern, wie Projekte zu erstellen und Kompilieren von Code steuern.