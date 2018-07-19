---
title: 'Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118857"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Gewusst wie: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben
  Erstellen, bereinigen und Überprüfen eines SharePoint-Pakets (*.wsp*) mithilfe der Befehlszeile MSBuild-Aufgaben auf einem Entwicklungscomputer. Sie können diese Befehle auch verwenden, um den Buildprozess automatisieren, indem Sie mit Team Foundation Server auf einem Buildcomputer.  
  
## <a name="build-a-sharepoint-package"></a>Erstellen eines SharePoint-Pakets  
  
#### <a name="to-build-a-sharepoint-package"></a>Erstellen ein SharePoint-Pakets  
  
1.  Auf der Windows **starten** Menü wählen **Programme** > **Zubehör** > **Eingabeaufforderung**.  
  
2.  Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl zum Erstellen eines Pakets für das Projekt aus. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Beispielsweise können Sie eine der folgenden Befehle, um ein SharePoint-Projekt namens "ListDefinition1" Paket ausführen.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Bereinigen eines SharePoint-Pakets  
  
#### <a name="to-clean-a-sharepoint-package"></a>Zum Bereinigen eines SharePoint-Pakets  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl aus, um ein Paket für das Projekt zu bereinigen. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Beispielsweise können Sie eine der folgenden Befehle, um ein SharePoint-Projekt namens ListDefinition1 bereinigen ausführen.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Ein SharePoint-Paket überprüfen  
  
#### <a name="to-validate-a-sharepoint-package"></a>So überprüfen Sie eine SharePoint-Paket  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl aus, um ein Paket für das Projekt zu überprüfen. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Beispielsweise können Sie eine der folgenden Befehle, um ein SharePoint-Projekt namens ListDefinition1 überprüfen ausführen.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Festlegen von Eigenschaften in einem SharePoint-Paket  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Zum Festlegen einer Eigenschaft in einem SharePoint-Paket  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl zum Festlegen einer Eigenschaft in ein Paket für das Projekt aus. Ersetzen Sie dies *PropertyName* mit der Eigenschaft, die Sie festlegen möchten.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl aus, um die Warnstufe festlegen ausführen.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von SharePoint-features](../sharepoint/creating-sharepoint-features.md)   
 [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
