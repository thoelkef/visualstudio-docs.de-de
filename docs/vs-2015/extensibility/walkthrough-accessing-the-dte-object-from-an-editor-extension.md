---
title: 'Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148874"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt über eine Editor-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In VSPackages können Sie das DTE-Objekt abrufen, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode mit dem Typ des DTE-Objekts aufrufen. In Managed Extensibility Framework-Erweiterungen (MEF) können Sie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> die-Methode mit dem Typ importieren und anschließend aufzurufen <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Das DTE-Objekt wird erhalten.  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>So erhalten Sie das DTE-Objekt aus Service Provider  
  
1. Erstellen Sie ein c#-VSIX-Projekt mit dem Namen `DTETest` . Fügen Sie eine Editor-Klassifizierungs Element Vorlage hinzu, und benennen Sie Sie `DTETest` . Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Fügen Sie dem Projekt die folgenden Assemblyverweise hinzu:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. immutable. 10.0  
  
3. Wechseln Sie zur Datei DTETest.cs, und fügen Sie die folgenden `using` Anweisungen hinzu:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. Importieren Sie in der- `GetDTEProvider` Klasse <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. Fügen Sie folgenden Code in die `GetClassifier()`-Methode ein.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Wenn Sie die- <xref:EnvDTE80.DTE2> Schnittstelle verwenden müssen, können Sie das DTE-Objekt in das DTE-Objekt umwandeln.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)
