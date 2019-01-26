---
title: Managed Extensibility Framework im Editor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df5edaeab56a05b6bb3fbafc371ec3ac4089cacc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917966"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Das Managed Extensibility Framework im editor
Der Editor wird mit Komponenten des Managed Extensibility Framework (MEF) erstellt. Können Sie Ihre eigenen MEF-Komponenten, um den Editor zu erweitern, erstellen und Ihren Code kann auch Komponenten-Editors nutzen.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über das Managed Extensibility Framework  
 Das MEF ist eine .NET Bibliothek, mit dem Sie das Hinzufügen und ändern die Funktionen einer Anwendung oder Komponente, die das MEF-Programmiermodell entspricht. Visual Studio-Editor kann sowohl bereitstellen und Nutzen von MEF-Komponenten.  
  
 Das MEF befindet sich in .NET Framework, Version 4 *System.ComponentModel.Composition.dll* Assembly.  
  
 Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Komponenten und Kompositionscontainer  
 Eine Komponente ist eine Klasse oder ein Member einer Klasse, die eine (oder beides) der folgenden Möglichkeiten:  
  
- Nutzen Sie eine andere Komponente  
  
- Von einer anderen Komponente verwendet werden  
  
  Betrachten Sie beispielsweise eine einkaufsanwendung, die eine Eintrag-Komponente, die von der Verfügbarkeit Produktdaten, die von einer Komponente der Warehouse-Inventur bereitgestellten abhängt. Gemäß MEF, das Teil der Hardwareinventur kann *exportieren* Verfügbarkeit von Produktdaten und die Reihenfolge Eintrag Teil kann *importieren* Daten. Der Eintrag Reihenfolge und den Bestandteil müssen nicht voneinander wissen; die *Kompositionscontainer* (bereitgestellt von der hostanwendung) Dient zum Verwalten des Satz von Exporten und Auflösen von Exporte und Importe.  
  
  Der Kompositionscontainer <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ist in der Regel im Besitz des Hosts. Der Kompositionscontainer verwaltet eine *Katalog* von exportierten Komponenten.  
  
### <a name="export-and-import-component-parts"></a>Exportieren und Importieren von Komponenten  
 Sie können alle Funktionen, exportieren, sofern es als eine öffentliche Klasse oder einen öffentlichen Member einer Klasse (Eigenschaft oder Methode) implementiert ist. Sie müssen keine leiten Sie Ihre Komponente von <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Sie müssen stattdessen Hinzufügen einer <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut auf die Klasse oder Klassenmember, die Sie exportieren möchten. Dieses Attribut gibt an, die *Vertrag* durch die eine andere Komponente Teil Ihrer Funktionen zur importieren kann.  
  
### <a name="the-export-contract"></a>Der Export-Vertrag  
 Die <xref:System.ComponentModel.Composition.ExportAttribute> definiert die Entität (Klasse, Schnittstelle oder Struktur), die exportiert wird. In der Regel verwendet das Export-Attribut einen Parameter, der den Typ des Exports angibt.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 In der Standardeinstellung die <xref:System.ComponentModel.Composition.ExportAttribute> Attribut definiert einen Vertrag, der den Typ der Klasse exportieren.  
  
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
  
### <a name="import-a-mef-export"></a>Importieren Sie einen MEF-Export  
 Wenn Sie einen MEF-Export nutzen möchten, benötigen Sie den Vertrag (in der Regel den Typ), mit dem sie exportiert wurde, und fügen, eine <xref:System.ComponentModel.Composition.ImportAttribute> Attribut, dem dieser Wert ist. Standardmäßig verwendet das Import-Attribut einen Parameter, der den Typ der Klasse ist, das geändert wird. Die folgenden Zeilen des Imports der Code die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Typ.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>Rufen Sie die Editor-Funktionen aus einer MEF-Komponente  
 Wenn Ihr vorhandene Code einer MEF-Komponente ist, können Sie MEF-metadatenexport, Editor-Komponenten nutzen.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Editor-Funktionen aus einer MEF-Komponente verwenden  
  
1.  Fügen Sie Verweise auf *System.Composition.ComponentModel.dll*, befindet sich im globalen Assemblycache (GAC), und die Editor-Assemblys.  
  
2.  Hinzufügen der entsprechenden using-Anweisungen.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Hinzufügen der `[Import]` wie folgt zu Ihrer Schnittstelle Service-Attributs.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Wenn Sie den Dienst erhalten haben, können Sie eine der zugehörigen Komponenten nutzen.  
  
5.  Wenn Sie kompiliert die Assembly, und fügen Sie ihn in die *... \Common7\IDE\Components\* Ordner von Visual Studio-Installation.  
  
## <a name="see-also"></a>Siehe auch  
 [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)