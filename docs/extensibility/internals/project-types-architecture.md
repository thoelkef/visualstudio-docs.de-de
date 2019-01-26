---
title: Architektur von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85ae75501e705ef126ac11c3b13672b1713e7735
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033725"
---
# <a name="project-types-architecture"></a>Architektur von Projekttypen
Dieser Abschnitt enthält ausführliche Informationen zur Architektur von Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)  
 Listet die Dienste, die ein Projekttyp nutzen kann und die Schnittstellen, die sie implementieren muss.  
  
 [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)  
 Beschreibt die Schnittstellen Projekttypen müssen implementieren und optional implementieren können, um zusätzliche Funktionen bereitzustellen.  
  
 [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)  
 Geben Sie die erleichtert Ihnen die Entscheidung, wenn Sie ein Projekt erstellen müssen und Sie können beim Verwenden einer anderen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Erweiterbarkeitsfunktion wie VSPackages und Editoren, um das gleiche Ziel zu erreichen.  
  
 [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hierarchien und Auswahlkontext verwendet, um eine konsistente und vereinfachte Benutzeroberfläche bereitzustellen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)  
 Erläutert, wie Sie das Verhalten der Projektsysteme von Anpassen von Projektuntertypen ermöglichen [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Bietet eine Übersicht über Projekte als die grundlegenden Bausteine von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Links werden zu weiteren Themen bereitgestellt, die erläutern, wie Projekte zu erstellen und Kompilieren von Code steuern.