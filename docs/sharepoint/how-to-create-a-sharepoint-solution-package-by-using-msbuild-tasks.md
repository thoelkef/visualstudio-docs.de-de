---
title: "Gewusst wie: Erstellen eines SharePoint-L&#246;sungspakets mithilfe von MSBuild-Zielen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Pakete"
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Erstellen eines SharePoint-L&#246;sungspakets mithilfe von MSBuild-Zielen
  Mit MSBuild\-Befehlszeilenaufgaben auf einem Entwicklungscomputer können Sie ein SharePoint\-Paket \(.wsp\) erstellen, bereinigen und überprüfen.  Sie können diese Befehle auch verwenden, um den Buildprozess mit Team Foundation Server auf einem Buildcomputer zu automatisieren.  
  
## Erstellen eines SharePoint\-Pakets  
  
#### So erstellen Sie ein SharePoint\-Paket  
  
1.  Wählen Sie im Windows\-Menü **Start** die Optionen **Zubehör**, **EingabeaufforderungAlle Programme** aus.  
  
2.  Wechseln Sie zu dem Verzeichnis, in dem sich das SharePoint\-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu erstellen.  Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Sie können z. B. einen der folgenden Befehle ausführen, um ein SharePoint\-Projekt mit dem Namen "ListDefinition1" zu verpacken.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## Bereinigen eines SharePoint\-Pakets  
  
#### So bereinigen Sie ein SharePoint\-Paket  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Wechseln Sie zu dem Verzeichnis, in dem sich das SharePoint\-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu bereinigen.  Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Sie können z. B. einen der folgenden Befehle ausführen, um ein SharePoint\-Projekt mit dem Namen "ListDefinition1" zu bereinigen.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## Überprüfen eines SharePoint\-Pakets  
  
#### So überprüfen Sie ein SharePoint\-Paket  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Wechseln Sie zu dem Verzeichnis, in dem sich das SharePoint\-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu überprüfen.  Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Sie können z. B. einen der folgenden Befehle ausführen, um ein SharePoint\-Projekt mit dem Namen "ListDefinition1" zu überprüfen.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## Festlegen von Eigenschaften in einem SharePoint\-Paket  
  
#### So legen Sie eine Eigenschaft in einem SharePoint\-Paket fest  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Wechseln Sie zu dem Verzeichnis, in dem sich das SharePoint\-Projekt befindet.  
  
3.  Geben Sie den folgenden Befehl ein, um eine Eigenschaft in einem Paket für das Projekt festzulegen.  Ersetzen Sie *PropertyName* durch die Eigenschaft, die Sie festlegen möchten.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Sie können beispielsweise den folgenden Befehl ausführen, um die Warnstufe festzulegen.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## Siehe auch  
 [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md)   
 [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  