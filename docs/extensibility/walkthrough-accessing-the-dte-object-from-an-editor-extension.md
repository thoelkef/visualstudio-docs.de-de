---
title: 'Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1319e539c185a231637b4e78d7ac0de9154ed8a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953048"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung
In VSPackages, erhalten Sie das DTE-Objekt durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekt. In Erweiterungen des Managed Extensibility Framework (MEF), können Sie importieren <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> und rufen Sie dann die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode mit dem Typ <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="getting-the-dte-object"></a>Abrufen des DTE-Objekts

### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Um das DTE-Objekt über den ServiceProvider zu erhalten.

1. Erstellen Sie ein C#-VSIX-Projekt mit dem Namen `DTETest`. Hinzufügen einer Elementvorlage-Editor-Klassifizierung aus, und nennen Sie sie `DTETest`. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Wechseln Sie zu der *DTETest.cs* Datei, und fügen Sie die folgenden `using` Anweisungen:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio.Shell;

    ```

4. In der `GetDTEProvider` Klasse, importieren Sie eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;

    ```

5. Fügen Sie folgenden Code in die `GetClassifier()`-Methode ein.

    ```csharp
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));

    ```

6. Wenn Sie verwenden die <xref:EnvDTE80.DTE2> -Schnittstelle können Sie das DTE-Objekt, umgewandelt.

## <a name="see-also"></a>Siehe auch
- [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)