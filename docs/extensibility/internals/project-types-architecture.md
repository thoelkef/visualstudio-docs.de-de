---
title: "Architektur für Projekttypen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86ff1ed0b616eb52d57755e7537642e4f086c1f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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