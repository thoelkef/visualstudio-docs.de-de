---
title: Übersicht über benutzerdefinierte Dokumenteigenschaften
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 11c344b683a67f369ef3848a41b7907622945ffa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866856"
---
# <a name="custom-document-properties-overview"></a>Übersicht über benutzerdefinierte Dokumenteigenschaften

Wenn Sie ein Projekt auf Dokumentebene erstellen, fügt Visual Studio zwei benutzerdefinierte Eigenschaften auf das Dokument im Projekt: \_AssemblyLocation und \_AssemblyName. Wenn ein Benutzer ein Dokument öffnet, überprüft Microsoft Office-Anwendung für diese benutzerdefinierte Dokumenteigenschaften. Wenn sie im Dokument vorhanden sind, um die Anwendung lädt die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die die Anpassung startet. Weitere Informationen finden Sie unter [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Diese Eigenschaft enthält die CLSID einer Schnittstelle in der Office-Lösung Loader-Komponente von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Der CLSID-Wert ist 4-491E-A7D4-64AF99AF6E8B-4E3C66D5 - 58D. Sie sollten diesen Wert nicht ändern.

## <a name="assemblylocation"></a>\_AssemblyLocation

Diese Eigenschaft enthält eine Zeichenfolge, die Details zum Bereitstellungsmanifest für die Anpassung enthält. Weitere Informationen zu Manifesten finden Sie unter [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Die \_AssemblyLocation-Eigenschaftswert verfügen kann verschiedene Formate, je nachdem, wie die Lösung bereitgestellt wird:

- Wenn die Projektmappe veröffentlicht wird, um von einer Website, UNC-Pfad oder ein CD oder USB-Laufwerk installiert werden, hat die _AssemblyLocation-Eigenschaft das Format *DeploymentManifestPath*|*SolutionID*. Die folgende Zeichenfolge ist ein Beispiel:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Wenn Sie ausführen oder Debuggen der Projektmappe in Visual Studio, hat die _AssemblyLocation-Eigenschaft das Format *DeploymentManifestName*|*SolutionID*| Vstolocal. Die folgende Zeichenfolge ist ein Beispiel:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  Die *SolutionID* ist eine GUID, die die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zum Identifizieren der Lösung verwendet. Die *SolutionID* wird automatisch generiert, wenn Sie das Projekt erstellen. Die **Vstolocal** -Begriff gibt an, um die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , dass die Assembly aus dem gleichen Ordner wie das Dokument geladen werden soll.

## <a name="see-also"></a>Siehe auch

- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md)
- [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Vorgehensweise: Veröffentlichen einer Office-Projektmappe mit ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
