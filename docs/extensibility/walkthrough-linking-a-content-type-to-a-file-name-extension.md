---
title: "Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfe19b8733a6ee5ffe3d038778e664a4a1455dbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung
Sie können eigene Inhaltstyp definieren und verknüpfen Sie eine Dateinamenerweiterung darauf mit Managed Extensibility Framework (MEF) editorerweiterungen. In einigen Fällen wurde die Erweiterung bereits durch einen Sprachdienst definiert. dennoch müssen für die Verwendung mit MEF Sie weiterhin es einem Inhaltstyp verknüpfen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `ContentTypeTest`.  
  
2.  In der **"Source.Extension.vsixmanifest"** Datei, wechseln Sie zu der **Bestand** Registerkarte, und legen Sie die **Typ** Feld **Microsoft.VisualStudio.MefComponent**, **Quelle** Feld **ein Projekt in der aktuellen Projektmappe**, und die **Projekt** Feld auf den Namen des Projekts.  
  
## <a name="defining-the-content-type"></a>Definieren den Inhaltstyp  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `FileAndContentTypes`.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Fügen Sie die folgenden `using` Direktiven.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Deklarieren Sie eine statische Klasse, die die Definitionen enthält.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  In dieser Klasse Exportieren einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> mit dem Namen "ausgeblendet", und deklarieren Sie die Basisdefinition "Text" sein.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Verknüpfen eine Dateinamenerweiterung mit einem Inhaltstyp  
  
-   Um eine Dateinamenerweiterung diesen Inhaltstyp zuzuordnen, Exportieren einer <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , die über die Erweiterung "HID-Dateien" und der Inhaltstyp "ausgeblendet".  
  
    ```csharp  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Ein Export-Editor für hinzugefügt den Inhaltstyp  
  
1.  Erstellen Sie eine Editor-Erweiterung. Sie können z. B. die Rand Glyphe-Erweiterung, die in beschriebenen [Exemplarische Vorgehensweise: Erstellen eines Symbols Rand](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Fügen Sie die Klasse, die Sie in diesem Verfahren definiert.  
  
3.  Beim Exportieren der Erweiterungsklasse Hinzufügen einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> vom Typ "ausgeblendet" darauf.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)