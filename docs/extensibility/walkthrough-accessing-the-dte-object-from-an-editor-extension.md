---
title: Zugriff auf das DTE-Objekt aus einer Editor-Erweiterung
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878201"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugriff auf das DTE-Objekt aus einer Editor-Erweiterung

In VSPackages, erhalten Sie das DTE-Objekt durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekt. In Erweiterungen des Managed Extensibility Framework (MEF), können Sie importieren <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> und rufen Sie dann die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode mit dem Typ <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Vorraussetzungen

Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Ruft das DTE-Objekt

1. Erstellen Sie eine C# VSIX-Projekt, und nennen Sie sie **DTETest**. Hinzufügen einer **Editor Klassifizierer** Elementvorlagen, und nennen Sie sie **DTETest**.

   Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Fügen Sie die folgende Assemblyverweis auf das Projekt hinzu:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. In der *DTETestProvider.cs* Datei, fügen Sie die folgenden `using` Anweisungen:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. In der `DTETestProvider` Klasse, importieren Sie ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. In der `GetClassifier()` -Methode, fügen Sie den folgenden Code vor der `return` Anweisung:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. In der *DTETestProvider.cs* Datei, fügen Sie die folgenden `using` Anweisungen:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. In der `DTETestProvider` Klasse, importieren Sie ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. In der `GetClassifier()` -Methode, fügen Sie den folgenden Code vor der `return` Anweisung:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
- [Starten Sie Visual Studio mit DTE](launch-visual-studio-dte.md)