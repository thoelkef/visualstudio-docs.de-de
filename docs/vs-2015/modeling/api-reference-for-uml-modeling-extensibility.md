---
title: API-Referenz für UML-Modellierungs Erweiterbarkeit | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672805"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>API-Referenz für UML-Modellierungserweiterbarkeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Programmcode schreiben,um die Modelle, die Sie in Visual Studio erstellen, zu lesen und zu bearbeiten. Die API-Referenz enthält Informationen zu den spezifischen Klassen, die Sie dabei unterstützen. Weitere aufgabenorientierte Informationen finden Sie in den Themen unter [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md). Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Assemblys

|Assembly|Optionen|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Lesen und Ändern von Modellelementen, wie z. b. IUseCase, IAssociation usw.<br />-Navigieren Sie in Beziehungen zwischen Elementen.<br /><br /> Die Namespaces und Typen entsprechen denen, die in der UML-Spezifikation definiert sind.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Neue Instanzen von Modellelementen erstellen<br />-Zugreifen auf und Ändern von Formen und Diagrammen.|

## <a name="see-also"></a>Weitere Informationen
 [Erweitern von UML-Modellen und-Diagrammen API-](../modeling/extend-uml-models-and-diagrams.md) [Referenz für das Modellierungs-SDK für Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
