---
title: Erstellen von SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 432daff22616950e0a97164190a94082bf2db354
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401501"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben
  Erstellen, bereinigen und Überprüfen eines SharePoint-Pakets ( *.wsp*) mithilfe der Befehlszeile MSBuild-Aufgaben auf einem Entwicklungscomputer. Sie können diese Befehle auch verwenden, um den Buildprozess automatisieren, indem Sie mit Team Foundation Server auf einem Buildcomputer.

## <a name="build-a-sharepoint-package"></a>Erstellen eines SharePoint-Pakets

#### <a name="to-build-a-sharepoint-package"></a>Erstellen ein SharePoint-Pakets

1. Auf der Windows **starten** Menü wählen **Programme** > **Zubehör** > **Eingabeaufforderung**.

2. Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl zum Erstellen eines Pakets für das Projekt aus. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.

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

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl aus, um ein Paket für das Projekt zu bereinigen. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.

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

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl aus, um ein Paket für das Projekt zu überprüfen. Ersetzen Sie dies *ProjectFileName* mit dem Namen des Projekts.

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

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Ändern Sie in das Verzeichnis, in dem das SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl zum Festlegen einer Eigenschaft in ein Paket für das Projekt aus. Ersetzen Sie dies *PropertyName* mit der Eigenschaft, die Sie festlegen möchten.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Beispielsweise können Sie den folgenden Befehl aus, um die Warnstufe festlegen ausführen.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Siehe auch
- [Erstellen von SharePoint-features](../sharepoint/creating-sharepoint-features.md)
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
