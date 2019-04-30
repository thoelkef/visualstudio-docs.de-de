---
title: 'Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16f3a33ff273b62c701eae66d8fda1ff7178c5c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965040"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung
Sie können einen eigenen Inhaltstyp definieren, und verknüpfen eine Dateinamenerweiterung, mit dem Managed Extensibility Framework (MEF) Erweiterungen des Editors. In einigen Fällen ist die Erweiterung bereits von einem Sprachdienst definiert. Aber für die Verwendung mit MEF muss weiterhin die Verknüpfung an einen Inhaltstyp.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `ContentTypeTest`.

2. In der **"Source.Extension.vsixmanifest"** -Datei, wechseln Sie zu der **Assets** , und legen die **Typ** Feld **Microsoft.VisualStudio.MefComponent**, **Quelle** Feld **ein Projekt in der aktuellen Projektmappe**, und die **Projekt** Feld auf den Namen des Projekts.

## <a name="define-the-content-type"></a>Definieren Sie den Inhaltstyp

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `FileAndContentTypes`.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Fügen Sie die folgenden `using` Anweisungen.

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

5. In dieser Klasse Exportieren einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> mit dem Namen "hid", und deklarieren Sie die Basisdefinition "Text" sein.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Verknüpfen Sie eine Dateinamenerweiterung mit einem Inhaltstyp

- Um eine Dateinamenerweiterung dieser Inhaltstyp zuzuordnen, Exportieren einer <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , die die Erweiterung hat *HID-Dateien* und der Inhaltstyp "hid".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Hinzufügen des Inhaltstyps mit einem Editor-export

1. Erstellen einer Editor-Erweiterungs. Sie können z. B. die Rand Symbol-Erweiterung, die in beschriebenen [Exemplarische Vorgehensweise: Erstellen eine randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Fügen Sie der Klasse, die Sie in diesem Verfahren definiert.

3. Beim Exportieren der Erweiterungsklasse Hinzufügen einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> vom Typ "hid" zuzuweisen.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Siehe auch
- [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)