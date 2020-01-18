---
title: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269092"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung

In VSPackages können Sie das DTE-Objekt abrufen, indem Sie die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>-Methode mit dem Typ des DTE-Objekts aufrufen. In Managed Extensibility Framework-Erweiterungen (MEF) können Sie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> importieren und dann die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>-Methode mit dem Typ <xref:EnvDTE.DTE>aufzurufen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>DTE-Objekt

1. Erstellen Sie C# ein VSIX-Projekt, und nennen Sie es **dtetest**. Fügen Sie eine **Editor-Klassifizierungs** Element Vorlage hinzu, und nennen Sie Sie **dtetest**.

   Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Fügen Sie in der Datei *DTETestProvider.cs* die folgenden `using` Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren Sie in der `DTETestProvider`-Klasse eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen Sie in der `GetClassifier()`-Methode den folgenden Code vor der `return`-Anweisung hinzu:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Fügen Sie in der Datei *DTETestProvider.cs* die folgenden `using` Direktiven hinzu:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Importieren Sie in der `DTETestProvider`-Klasse eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Fügen Sie in der `GetClassifier()`-Methode den folgenden Code vor der `return`-Anweisung hinzu:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
- [Starten von Visual Studio mit DTE](launch-visual-studio-dte.md)
