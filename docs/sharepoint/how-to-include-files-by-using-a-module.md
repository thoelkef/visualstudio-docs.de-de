---
title: "Gewusst wie: Einschlie&#223;en von Dateien mithilfe eines Moduls"
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
  - "Module [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Module"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Gewusst wie: Einschlie&#223;en von Dateien mithilfe eines Moduls
  Bei *Modulen* \(nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Modulen\) handelt es sich um Container, die es Ihnen ermöglichen, Dateien wie ASPX\-Gestaltungsvorlagen, Textdateien oder Bilder für SharePoint bereitzustellen.  
  
 Sie können wählen, ob Sie eine Datei in einer Dokumentbibliothek oder als normale Datei \(beispielsweise "default.aspx"\) außerhalb einer Dokumentbibliothek bereitstellen möchten.  Wenn Sie einer Dokumentbibliothek eine Datei hinzufügen möchten, geben Sie `Type="GhostableInLibrary"` im **File**\-Element als Attribut an.  Durch diese Einstellung wird SharePoint angewiesen, ein Listenelement zu erstellen, das der Bibliothek zusammen mit der Datei hinzugefügt wird.  Wenn Sie eine Datei außerhalb einer Dokumentbibliothek bereitstellen möchten, geben Sie entweder `Type="Ghostable"` an, oder lassen Sie das **Type**\-Attribut einfach weg.  
  
## Hinzufügen eines Moduls zu einer SharePoint\-Lösung  
  
#### So fügen Sie ein Modul hinzu  
  
1.  Öffnen oder erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint\-Projekt.  
  
     Weitere Informationen finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Neues Element hinzufügen** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  In der Liste der SharePoint\-Vorlagen, wählen Sie die Vorlage **Modul** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Dieser Schritt erstellt einen Knoten, die im Projekt Module1 ".  
  
4.  unter "Module1" löschen Sie die Datei Sample.txt\-.  
  
     "Sample.txt" ist in allen neuen Modulen als Beispiel enthalten und wird nicht benötigt. \(Hinweis: Durch Löschen der Datei wird auch der entsprechende Eintrag aus der Datei "Elements.xml" des Moduls entfernt.\)  
  
5.  Wenn die Dateien in SharePoint in einer bestimmten Ordnerstruktur bereitgestellt werden sollen, erstellen Sie die entsprechenden Ordner in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter "Module1" erstellt, indem Sie den Knoten Module1, und dann in der Menüleiste und **Neuer Ordner** auswählen, **Projekt** auswählen.  
  
6.  Wählen Sie den Ordner, in dem Sie die Datei hinzufügen möchten, und dann, auf der Menüleiste aus, wählen Sie **Vorhandenes Element hinzufügen**, **Projekt** aus.  
  
7.  Wählen Sie eine oder mehrere Dateien, die für SharePoint bereitstellen möchten, und dann die Schaltfläche **Hinzufügen** aus.  
  
     Wenn Sie dem Projekt eine Datei hinzufügen, wird der Datei "Elements.xml" des Moduls automatisch ein entsprechender Eintrag hinzugefügt.  Wenn das Projekt bereitgestellt wird, werden die Dateien auf den SharePoint\-Server kopiert, und zwar relativ zu dem Projektstammverzeichnis, das mithilfe des **Url**\-Attributs des **File**\-Elements angegeben ist \(beispielsweise `Url="Module1/New Folder/SomeFile.doc`\).  Verschieben Sie eine Datei, deren Bereitstellungsort Sie ändern möchten, entweder im Projektmappen\-Explorer in einen anderen Ordner, oder ändern Sie die **Url**\-Einstellung.  
  
8.  Fügen Sie in "Elements.xml" dem Eintrag jeder Datei, die in einer Dokumentbibliothek enthalten sein soll, das `Type="GhostableInLibrary"`\-Attribut an.  Beispiel:  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Stellen Sie das Projekt bereit.  
  
     Die Dateien werden an die angegebenen Orte in SharePoint kopiert.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  