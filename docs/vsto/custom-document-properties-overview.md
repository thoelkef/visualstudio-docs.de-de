---
title: "Übersicht über benutzerdefinierte Dokumenteigenschaften | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 672eaf3ed82a80983b919a37b2aeff4c99621f43
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2018
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview

Wenn Sie ein Projekt auf Dokumentebene erstellen, fügt Visual Studio zwei benutzerdefinierte Eigenschaften auf das Dokument im Projekt: \_AssemblyLocation und \_AssemblyName. Wenn ein Benutzer ein Dokument öffnet, überprüft die Microsoft Office-Anwendung für diese benutzerdefinierte Dokumenteigenschaften. Wenn sie im Dokument vorhanden sind, lädt die Anwendung die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die die Anpassung startet. Weitere Informationen finden Sie unter [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Diese Eigenschaft enthält die CLSID einer Schnittstelle in der Office-Lösung-Ladeprogramm-Komponente von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Der CLSID-Wert ist 4-491E-A7D4-64AF99AF6E8B-4E3C66D5 - 58D. Sie sollten diesen Wert nie ändern.

## <a name="assemblylocation"></a>\_AssemblyLocation

Diese Eigenschaft enthält eine Zeichenfolge, die Details über das Bereitstellungsmanifest für die Anpassung bereitstellt. Weitere Informationen zu Manifesten finden Sie unter [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 The_AssemblyLocation-Eigenschaftswert kann verschiedene Formate haben je nach Art der Bereitstellung der Projektmappe aufweisen:

- Wenn die Projektmappe veröffentlicht wird, um von einer Website, UNC-Pfad oder eine CD oder einem USB-Laufwerk installiert werden, wird die _AssemblyLocation-Eigenschaft weist das Format *DeploymentManifestPath*|*SolutionID*. Die folgende Zeichenfolge ist ein Beispiel:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Wenn Sie ausführen oder Debuggen der Projektmappe aus Visual Studio, die _AssemblyLocation-Eigenschaft weist das Format auf *DeploymentManifestName*|*SolutionID*| Vstolocal. Die folgende Zeichenfolge ist ein Beispiel:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 Die *SolutionID* ist eine GUID, die die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verwendet, um die Projektmappe zu identifizieren. Die *SolutionID* wird automatisch generiert, wenn Sie das Projekt erstellen. Die **Vstolocal** -Begriff gibt an, um die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , dass die Assembly aus dem gleichen Ordner wie das Dokument geladen werden soll.

## <a name="see-also"></a>Siehe auch

[Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
[Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)
[-Anwendungsmanifest und-Bereitstellungsmanifest in Office-Projektmappen ](../vsto/application-and-deployment-manifests-in-office-solutions.md) 
 [Vorgehensweise: Veröffentlichen einer Office-Projektmappe mithilfe von ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
[Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
