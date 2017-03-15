---
title: Managed Extensibility Framework im Editor | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework im Editor
Der Editor wird mit Managed Extensibility Framework (MEF)-Komponenten erstellt. Sie können Ihre eigenen MEF-Komponenten zum Erweitern des Editors erstellen und Code kann auch Komponenten-Editors nutzen.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über das Managed Extensibility Framework  
 Das MEF ist ein .NET-Bibliothek, mit dem Sie das Hinzufügen und Ändern von Funktionen einer Anwendung oder Komponente, die das MEF-Programmiermodell folgt. Der Visual Studio-Editor kann sowohl bereitstellen und nutzen MEF-Komponenten.  
  
 Das MEF ist in .NET Framework Version 4 System.ComponentModel.Composition.dll-Assembly enthalten.  
  
 Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Komponenten und der Kompositionscontainer  
 Eine Komponente ist eine Klasse oder ein Member einer Klasse, die eine (oder beide) der folgenden möglich:  
  
-   Nutzen Sie eine andere Komponente  
  
-   Von einer anderen Komponente verwendet werden  
  
 Betrachten Sie z. B. eine Warenkorb-Anwendung, die Komponente einen Eintrag Produkt Verfügbarkeitsdaten, die von einer Komponente der Warehouse-Inventur bereitgestellten abhängt. MEF ausgedrückt, das Teil der Hardwareinventur kann *exportieren* Verfügbarkeit von Produktdaten und die Reihenfolge Eintrag Teil kann *importieren* Daten. Der Eintrag Reihenfolge und die Inventur Webpart müssen nicht voneinander wissen müssen. die *Kompositionscontainer* (bereitgestellt vom Host-Anwendung) ist verantwortlich für das Verwalten des Satz von Exporten und Auflösen von Exporte und importiert.  
  
 Der Kompositionscontainer <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, in der Regel vom Host gehört.</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> Der Kompositionscontainer verwaltet eine *Katalog* exportierten Komponenten.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportieren und Importieren von Komponenten  
 Sie können alle Funktionen exportieren, als es als eine öffentliche Klasse oder einen öffentlichen Member einer Klasse (Eigenschaft oder Methode) implementiert ist. Sie müssen keine Ihrer Komponente abgeleitet <xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart> Sie müssen stattdessen Hinzufügen einer <xref:System.ComponentModel.Composition.ExportAttribute>-Attribut auf die Klasse oder einen Klassenmember, die Sie exportieren möchten.</xref:System.ComponentModel.Composition.ExportAttribute> Dieses Attribut gibt die *Vertrag* durch die eine andere Komponente Teil Ihrer Funktionalität importieren kann.  
  
### <a name="the-export-contract"></a>Der Export-Vertrag  
 Die <xref:System.ComponentModel.Composition.ExportAttribute>definiert die Entität (Klasse, Schnittstelle oder Struktur) an, der exportiert wird.</xref:System.ComponentModel.Composition.ExportAttribute> In der Regel dauert das Export-Attribut einen Parameter, der den Typ des Exports angibt.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Standardmäßig das <xref:System.ComponentModel.Composition.ExportAttribute>Attribut definiert einen Vertrag, der den Typ des ausführenden Klasse ist</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Im Beispiel ist die Standardeinstellung `[Export]` Attribut entspricht `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Sie können auch eine Eigenschaft oder Methode, exportieren, wie im folgenden Beispiel gezeigt.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importieren einen MEF-Export  
 Wenn Sie einen MEF-Export nutzen möchten, benötigen Sie den Vertrag (i. d. r. der Typ), mit dem sie exportiert wurde, und fügen, eine <xref:System.ComponentModel.Composition.ImportAttribute>-Attribut den Wert aufweist.</xref:System.ComponentModel.Composition.ImportAttribute> Standardmäßig verwendet das Import-Attribut einen Parameter, der den Typ der Klasse ist, das geändert wird. Die folgenden Codezeilen Einlesen der <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>Typ.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Abrufen von-Editor-Funktionen aus einer MEF-Komponente  
 Wenn der vorhandene Code einer MEF-Komponente ist, können Sie MEF-Metadaten, EditorParts Komponente nutzen.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Nutzen der Funktionen des Editors aus einer MEF-Komponente  
  
1.  Fügen Sie Verweise auf System.Composition.ComponentModel.dll, die im globalen Assemblycache (GAC) befindet, und auf die Editor-Assemblys.  
  
2.  Hinzufügen der entsprechenden using-Anweisungen.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Hinzufügen der `[Import]` -Attribut auf die Dienstschnittstelle, wie folgt.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Wenn Sie den Dienst erhalten haben, können Sie eine der zugehörigen Komponenten nutzen.  
  
5.  Wenn Sie kompiliert die Assembly, und fügen Sie ihn in das... \Common7\IDE\Components\ Ordner der Visual Studio-Installation.  
  
## <a name="see-also"></a>Siehe auch  
 [Language Service und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)
