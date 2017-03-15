---
title: "Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neu – das DTE-Objekt abrufen"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In VSPackages, erhalten Sie das DTE\-Objekt durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> \-Methode mit dem Typ des DTE\-Objekts. In Managed Extensibility Framework \(MEF\)\-Erweiterungen, importieren Sie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> und rufen Sie dann die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode mit einem <xref:EnvDTE.DTE>.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Abrufen des DTE\-Objekts  
  
#### Das DTE\-Objekt aus dem ServiceProvider abgerufen  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt namens `DTETest`. Hinzufügen einer Elementvorlage Classifier\-Editor, und nennen Sie es `DTETest`. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Wechseln Sie zur Datei DTETest.cs, und fügen Sie die folgenden `using` Direktiven:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  In der `GetDTEProvider` Klasse, importieren Sie eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Fügen Sie folgenden Code in die `GetClassifier()`\-Methode ein.  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Wenn Sie verwenden die <xref:EnvDTE80.DTE2> \-Schnittstelle können Sie das DTE\-Objekt, umgewandelt.  
  
## Siehe auch  
 [Language Service und Erweiterungspunkte\-Editor](../extensibility/language-service-and-editor-extension-points.md)