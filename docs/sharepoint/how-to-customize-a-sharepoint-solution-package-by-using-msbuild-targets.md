---
title: "Gewusst wie: Anpassen eines SharePoint-L&#246;sungspakets mithilfe von MSBuild-Zielen"
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
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Anpassen eines SharePoint-L&#246;sungspakets mithilfe von MSBuild-Zielen
  Mithilfe MSBuild\-Ziele an einer Eingabeaufforderung verwenden, können Sie anpassen, wie Visual Studio SharePoint\-Paketdateien \(.wsp\) erstellt.  Beispielsweise können Sie die MSBuild\-Eigenschaften anpassen, die das Zwischenverzeichnis für das und die MSBuild\-Elementgruppen zu ändern, die die aufgelisteten Dateien angeben.  
  
## Anpassen und Ausführen von MSBuild\-Zielen  
 Wenn Sie das BeforeLayout\-Ziel und das AfterLayout\-Ziel zum anpassen, können Sie Aufgaben vor Paketlayout, wie Hinzufügen, Entfernen oder Ändern von Dateien ausführen, die eingebunden werden.  
  
#### So passen Sie das BeforeLayout\-Ziel an  
  
1.  Öffnen Sie einen Editor, z Editor, und fügen Sie dann den folgenden Code hinzu.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Dieses Beispiel zeigt eine Meldung vor der Verpackung dieses Ziels an.  
  
2.  Nennen Sie die Datei **CustomLayout.SharePoint.targets**, und speichern Sie diese im Ordner für das SharePoint\-Projekt.  
  
3.  Öffnen Sie das Projekt, öffnen Sie sein Kontextmenü, und wählen Sie dann **Projekt entladen** aus.  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projekt, und wählen Sie *ProjectName***.vbproj** oder **Bearbeiten***ProjectName***.csprojBearbeiten** aus.  
  
5.  Nachdem `Import` die Zeile neben dem Ende der Projektdatei, die folgende Zeile hinzu.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Speichern und schließen Sie die Projektdatei.  
  
7.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Projekt erneut laden** aus.  
  
 Wenn Sie das Projekt veröffentlichen, wird die Meldung in der Ausgabe, bevor das Verpacken beginnt.  
  
#### So passen Sie das AfterLayout\-Ziel an  
  
1.  Klicken Sie auf der Menüleiste **Öffnen**, **Datei**, **Datei** aus.  
  
2.  Im Dialogfeld **Datei öffnen** Navigieren Sie zum Projektordner, wählen Sie die CustomLayout.target\-Datei, und wählen Sie dann die Schaltfläche **Öffnen** aus.  
  
3.  Kurz bevor das `</Project>`\-Tag, den folgenden Code hinzufügen:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Dieses Beispiel zeigt eine Meldung an, nachdem dieses Ziel gepackt ist.  
  
4.  Speichern und schließen Sie die Zieldatei.  
  
5.  Starten Sie Visual Studio neu und öffnen Sie dann das Projekt.  
  
 Wenn Sie das Projekt veröffentlichen, wird die BeforeLayout\-Meldung, bevor das Verpacken von Anfang und von AfterLayout\-Meldung wird, nachdem verpacken beendet.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  