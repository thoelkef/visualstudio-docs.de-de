---
title: 'Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697088"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung
Sie können Ihren eigenen Inhaltstyp definieren und eine Dateinamenerweiterung mit ihm verknüpfen, indem Sie die MEF-Erweiterung (Managed Extensibility Framework) des Editors verwenden. In einigen Fällen ist die Dateinamenerweiterung bereits durch einen Sprachdienst definiert. Um es jedoch mit MEF verwenden zu können, müssen Sie es dennoch mit einem Inhaltstyp verknüpfen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `ContentTypeTest`die Lösung .

2. Wechseln Sie in der Datei **source.extension.vsixmanifest** zur Registerkarte **Assets,** und legen Sie das **Feld Typ** auf **Microsoft.VisualStudio.MefComponent**, das **Feld Quelle** auf Ein Projekt in der **aktuellen Projektmappe**und das **Feld Projekt** auf den Namen des Projekts fest.

## <a name="define-the-content-type"></a>Definieren des Inhaltstyps

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `FileAndContentTypes`.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Fügen Sie `using` die folgenden Direktiven hinzu.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Deklarieren Sie eine statische Klasse, die die Definitionen enthält.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. Exportieren Sie in <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> dieser Klasse einen benannten "hid" und deklarieren Sie seine Basisdefinition als "Text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Verknüpfen einer Dateinamenerweiterung mit einem Inhaltstyp

- Um diesen Inhaltstyp einer Dateinamenerweiterung <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> zuzuordnen, exportieren Sie eine mit der Erweiterung *.hid* und dem Inhaltstyp "hid".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Hinzufügen des Inhaltstyps zu einem Editorexport

1. Erstellen Sie eine Editorerweiterung. Sie können z. B. die in Walkthrough beschriebene Erweiterung der Randglyphen [verwenden: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Fügen Sie die Klasse hinzu, die Sie in dieser Prozedur definiert haben.

3. Wenn Sie die Erweiterungsklasse <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> exportieren, fügen Sie ihr einen Vom Typ "hid" hinzu.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
