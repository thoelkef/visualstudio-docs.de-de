---
title: Übersicht über benutzerdefinierte Dokumenteigenschaften
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>Übersicht über benutzerdefinierte Dokumenteigenschaften

Wenn Sie ein Projekt auf Dokumentebene erstellen, fügt Visual Studio zwei benutzerdefinierte Eigenschaften auf das Dokument im Projekt: \_AssemblyLocation und \_AssemblyName. Wenn ein Benutzer ein Dokument öffnet, überprüft die Microsoft Office-Anwendung für diese benutzerdefinierte Dokumenteigenschaften. Wenn sie im Dokument vorhanden sind, lädt die Anwendung die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die die Anpassung startet. Weitere Informationen finden Sie unter [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Diese Eigenschaft enthält die CLSID einer Schnittstelle in der Office-Lösung-Ladeprogramm-Komponente von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Der CLSID-Wert ist 4-491E-A7D4-64AF99AF6E8B-4E3C66D5 - 58D. Sie sollten diesen Wert nie ändern.

## <a name="assemblylocation"></a>\_AssemblyLocation

Diese Eigenschaft enthält eine Zeichenfolge, die Details über das Bereitstellungsmanifest für die Anpassung bereitstellt. Weitere Informationen zu Manifesten finden Sie unter [-Anwendungsmanifest und-Bereitstellungsmanifest in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 The_AssemblyLocation-Eigenschaftswert kann verschiedene Formate haben je nach Art der Bereitstellung der Projektmappe aufweisen:

- Wenn die Projektmappe veröffentlicht wird, um von einer Website, UNC-Pfad oder eine CD oder einem USB-Laufwerk installiert werden, wird die _AssemblyLocation-Eigenschaft weist das Format *DeploymentManifestPath*|*SolutionID*. Die folgende Zeichenfolge ist ein Beispiel:

     file://deployserver/myshare/ExcelWorkbook1.VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Wenn Sie ausführen oder Debuggen der Projektmappe aus Visual Studio, die _AssemblyLocation-Eigenschaft weist das Format auf *DeploymentManifestName*|*SolutionID*| Vstolocal. Die folgende Zeichenfolge ist ein Beispiel:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | Vstolocal

 Die *SolutionID* ist eine GUID, die die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verwendet, um die Projektmappe zu identifizieren. Die *SolutionID* wird automatisch generiert, wenn Sie das Projekt erstellen. Die **Vstolocal** -Begriff gibt an, um die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , dass die Assembly aus dem gleichen Ordner wie das Dokument geladen werden soll.

## <a name="see-also"></a>Siehe auch

- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)
- [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Vorgehensweise: Veröffentlichen einer Office-Projektmappe mithilfe von ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
