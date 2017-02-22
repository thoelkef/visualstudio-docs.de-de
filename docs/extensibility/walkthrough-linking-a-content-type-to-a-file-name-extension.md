---
title: "Exemplarische Vorgehensweise: Verkn&#252;pfen eines Inhaltstyps mit Erweiterung | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], verknüpfen Sie neu - Inhaltstyp mit Erweiterung"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Verkn&#252;pfen eines Inhaltstyps mit Erweiterung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können einen eigenen Inhaltstyp definieren und Erweiterung mithilfe von Managed Extensibility Framework \(MEF\) editorerweiterungen zu verknüpfen. In einigen Fällen wurde die Erweiterung bereits von einem Sprachdienst definiert. Dennoch muss für die Verwendung mit MEF noch es mit einen Inhaltstyp verknüpfen.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `ContentTypeTest`.  
  
2.  In der **source.extension.vsixmanifest** Datei, klicken Sie auf die **Bestand** Registerkarte, und legen Sie die **Typ** Feld **Microsoft.VisualStudio.MefComponent**,  **Quelle** Feld **ein Projekt in der aktuellen Projektmappe**, und die **Projekt** Feld auf den Namen des Projekts.  
  
## Den Inhaltstyp definieren  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `FileAndContentTypes`.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Fügen Sie die folgenden `using` Richtlinien.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Deklarieren Sie eine statische Klasse, die die Definitionen enthält.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Exportieren Sie in dieser Klasse eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> mit dem Namen "ausgeblendet", und deklarieren Sie die Basisdefinition "Text" sein.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## Verknüpfen eine Erweiterung zu einem Inhaltstyp  
  
-   Um eine Erweiterung dieser Inhaltstyp zuordnen möchten, Exportieren einer <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> die über die Erweiterung "HID\-Dateien" und der Inhaltstyp "ausgeblendet".  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## Der Inhaltstyp hinzugefügt ein Export\-Editor  
  
1.  Erstellen Sie eine Editor\-Erweiterung. Sie können z. B. die Rand Symbol\-Erweiterung in beschriebenen [Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Fügen Sie der Klasse, die Sie in diesem Verfahren definiert.  
  
3.  Beim Exportieren der Erweiterungsklasse hinzufügen ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> vom Typ "ausgeblendet" zu.  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## Siehe auch  
 [Language Service und Erweiterungspunkte\-Editor](../extensibility/language-service-and-editor-extension-points.md)