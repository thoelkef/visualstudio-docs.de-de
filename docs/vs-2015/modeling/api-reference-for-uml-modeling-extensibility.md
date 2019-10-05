---
title: API-Referenz für UML-Modellierungserweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12eadb9844df5da78b11367708fed715f1c13672
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159670"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>API-Referenz für UML-Modellierungserweiterbarkeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Programmcode schreiben,um die Modelle, die Sie in Visual Studio erstellen, zu lesen und zu bearbeiten. Die API-Referenz enthält Informationen zu den spezifischen Klassen, die Sie dabei unterstützen. Aufgabenorientierte Informationen finden Sie unter [Erweitern von UML-Modellen und Diagrammen](../modeling/extend-uml-models-and-diagrams.md). Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Assemblys  
  
|Assembly|Optionen|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|– Lesen und Ändern von Modellelementen, z. B. IUseCase, IAssociation usw.<br />-Navigieren Sie Beziehungen zwischen Elementen.<br /><br /> Die Namespaces und Typen entsprechen denen, die in der UML-Spezifikation definiert sind.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|– Erstellen Sie neue Instanzen von Modellelementen<br />-Zugriff auf und Ändern von Formen und Diagrammen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [API-Referenz für Modellierungs-SDK für Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
