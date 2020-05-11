---
title: Zugriff auf das DTE-Objekt über eine Editorerweiterung
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697660"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Greifen Sie über eine Editorerweiterung auf das DTE-Objekt zu

In VSPackages können Sie das DTE-Objekt abrufen, indem Sie die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekts aufrufen. In MEF-Erweiterungen (Managed Extensibility <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Framework) können <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Sie die <xref:EnvDTE.DTE>Methode mit einem Typ von importieren und dann aufrufen.

## <a name="prerequisites"></a>Voraussetzungen

Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Abrufen des DTE-Objekts

1. Erstellen Sie ein Projekt von C-VSIX, und nennen Sie es **DTETest**. Fügen Sie eine **Editor-Klassifierelementvorlage hinzu,** und nennen Sie sie **DTETest**.

   Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Fügen Sie in der `using` Datei *DTETestProvider.cs* die folgenden Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren `DTETestProvider` Sie in <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>der Klasse eine .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen `GetClassifier()` Sie in der Methode `return` den folgenden Code vor der Anweisung hinzu:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Fügen Sie in der `using` Datei *DTETestProvider.cs* die folgenden Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren `DTETestProvider` Sie in <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>der Klasse eine .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen `GetClassifier()` Sie in der Methode `return` den folgenden Code vor der Anweisung hinzu:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
- [Starten von Visual Studio mit DTE](launch-visual-studio-dte.md)
