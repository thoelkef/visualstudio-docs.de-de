---
title: Architektur für Projekttypen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6ef7fe6fbf4a8899606dca35c10745e68e3cbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-types-architecture"></a>Projektarchitektur-Typen
Dieser Abschnitt enthält ausführliche Informationen zur Architektur der Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)  
 Listet die Dienste, die ein Projekttyp verbraucht werden kann und Schnittstellen, die sie implementieren muss.  
  
 [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)  
 Beschreibt die Schnittstellen Projekttypen müssen implementieren und optional implementieren können, um zusätzliche Funktionalität bereitzustellen.  
  
 [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)  
 Geben Sie erleichtert Ihnen die Entscheidung, wenn Sie ein Projekt erstellen müssen und wenn Sie eine andere verwenden können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Erweiterbarkeitsfunktion wie VSPackages und Editoren, um das gleiche Ziel zu erreichen.  
  
 [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hierarchien und Auswahlkontext verwendet, um eine konsistente und vereinfachte Benutzeroberfläche bereitzustellen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)  
 Erläutert, wie Project Untertypen Anpassen des Verhaltens der Projektsystemen der können [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Bietet eine Übersicht über Projekte als die Grundbausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Links werden zu weiteren Themen bereitgestellt, die erläutern, wie Projekte steuern, erstellen und Kompilieren von Code.