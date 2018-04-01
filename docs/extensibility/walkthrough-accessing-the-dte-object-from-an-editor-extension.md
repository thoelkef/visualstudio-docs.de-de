---
title: 'Exemplarische Vorgehensweise: Zugreifen auf DTE-Objekt aus einer-Editor-Erweiterung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af14fa5f9a76e08a1fba3355e9391ce8229bd652
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugreifen auf DTE-Objekt aus einer-Editor-Erweiterung
In VSPackages, erhalten Sie das DTE-Objekt durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekts. In Managed Extensibility Framework (MEF)-Erweiterungen, importieren Sie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> und rufen Sie anschließend die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode mit einem <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Das DTE-Objekt abrufen  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Abrufen des DTE-Objekts aus ServiceProvider  
  
1.  Erstellen Sie ein C#-VSIX-Projekt namens `DTETest`. Hinzufügen einer Elementvorlage Klassifizierer-Editor, und nennen Sie sie `DTETest`. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Wechseln Sie zu der Datei DTETest.cs, und fügen Sie die folgenden `using` Direktiven:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  In der `GetDTEProvider` Klasse, importieren Sie eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Fügen Sie folgenden Code in die `GetClassifier()`-Methode ein.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Wenn Sie verwenden die <xref:EnvDTE80.DTE2> -Schnittstelle, können Sie das DTE-Objekt, umgewandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)