---
title: API-Referenz für UML-Modellierungserweiterbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: db042d59ce5f7363d9ed45e2baebbea45d3a0de4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515875"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>API-Referenz für UML-Modellierungserweiterbarkeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-API-Referenz für UML-UML-Modellierungserweiterbarkeit](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility).  
  
Sie können Programmcode schreiben,um die Modelle, die Sie in Visual Studio erstellen, zu lesen und zu bearbeiten. Die API-Referenz enthält Informationen zu den spezifischen Klassen, die Sie dabei unterstützen. Aufgabenorientierte Informationen finden Sie unter [Erweitern von UML-Modellen und Diagrammen](../modeling/extend-uml-models-and-diagrams.md). Welche Versionen von Visual Studio UML-Modelle unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Assemblys  
  
|Assembly|Optionen|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|– Lesen und Ändern von Modellelementen, z. B. IUseCase, IAssociation usw.<br />-Navigieren Sie Beziehungen zwischen Elementen.<br /><br /> Die Namespaces und Typen entsprechen denen, die in der UML-Spezifikation definiert sind.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|– Erstellen Sie neue Instanzen von Modellelementen<br />-Zugriff auf und Ändern von Formen und Diagrammen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [API-Referenz für Modellierungs-SDK für Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



