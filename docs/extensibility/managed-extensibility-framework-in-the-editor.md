---
title: Managed Extensibility Framework im Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c13b1a4e1b183b3a6f4b54f58cca3593ce5c7bb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework im Editor
Der Editor wird erstellt, mit Komponenten des Managed Extensibility Framework (MEF). Sie können eigene MEF-Komponenten zum Erweitern des Editors erstellen und Code kann auch Komponenten-Editors nutzen.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über das Managed Extensibility Framework  
 Das MEF ist eine .NET Bibliothek, mit dem Sie das Hinzufügen und ändern die Funktionen einer Anwendung oder Komponente, die das Programmiermodell von MEF folgt. Der Visual Studio-Editor kann sowohl bereitstellen und Nutzen von MEF-Komponententeilen.  
  
 Das MEF ist in .NET Framework Version 4 System.ComponentModel.Composition.dll-Assembly enthalten.  
  
 Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Komponenten und Kompositionscontainern  
 Eine Komponente ist eine Klasse oder ein Member einer Klasse, die eine (oder beide) der folgenden Maßnahmen kann:  
  
-   Nutzen Sie eine andere Komponente  
  
-   Von einer anderen Komponente genutzt werden  
  
 Betrachten Sie beispielsweise eine warenkorbanwendung, die eine Eintrag-Komponente verfügt, von die Verfügbarkeit Produktdaten, die von einer Komponente der Warehouse-Inventur bereitgestellten abhängt. MEF ausgedrückt, das Teil der Hardwareinventur kann *exportieren* Verfügbarkeit von Produktdaten und die Reihenfolge Eintrag Teil kann *importieren* Daten. Der Eintrag Reihenfolge und die Hardwareinventur-Webpart sind keine anderen kennen; die *Kompositionscontainer* (bereitgestellt von der hostanwendung) ist verantwortlich für die Verwaltung der Gruppe von Exporten und Auflösen von diesem exportiert und importiert.  
  
 Der Kompositionscontainer <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ist in der Regel im Besitz von dem Host. Der Kompositionscontainer verwaltet eine *Katalog* exportierten Komponenten.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportieren und Importieren von Komponenten  
 Sie können keine Funktionen exportieren, solange es als öffentliche Klasse oder einen öffentlichen Member einer Klasse (Eigenschaft oder Methode) implementiert wird. Sie müssen keine leiten Sie Ihre Komponente aus <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Sie müssen stattdessen Hinzufügen einer <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut auf die Klasse bzw. des Klassenmembers an, die Sie exportieren möchten. Dieses Attribut gibt an, die *Vertrag* durch die eine andere Komponente Teil Ihrer Funktionalität importiert werden kann.  
  
### <a name="the-export-contract"></a>Der Export-Vertrag  
 Die <xref:System.ComponentModel.Composition.ExportAttribute> definiert die Entität (Klasse, Schnittstelle oder Struktur), der exportiert wird. In der Regel wird die Export-Attribut ein Parameters, das den Typ des Exports angibt.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Wird standardmäßig die <xref:System.ComponentModel.Composition.ExportAttribute> Attribut definiert einen Vertrag, der den Typ des ausführenden Klasse ist.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Im Beispiel die Standardeinstellung `[Export]` Attribut entspricht dem `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Sie können auch eine Eigenschaft oder Methode, exportieren, wie im folgenden Beispiel gezeigt.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importieren von MEF-Export  
 Wenn Sie einen MEF-Export nutzen möchten, benötigen Sie den Vertrag (i. d. r. der Typ), mit der sie exportiert wurde, und fügen, eine <xref:System.ComponentModel.Composition.ImportAttribute> Attribut, das diesen Wert aufweist. Standardmäßig führt das Importattribut einen Parameter, der den Typ der Klasse ist, das geändert wird. Die folgenden Zeilen des Imports der Code die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Typ.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Abrufen von Editor-Funktionen aus einer MEF-Komponente  
 Wenn der vorhandene Code einer MEF-Komponente ist, können MEF-Metadaten Sie Editor Komponententeilen nutzen.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Editor-Funktionen aus einer MEF-Komponente zu nutzen  
  
1.  Fügen Sie Verweise hinzu, um System.Composition.ComponentModel.dll, die im globalen Assemblycache (GAC) befindet, und die Editor-Assemblys.  
  
2.  Fügen Sie das entsprechende using-Anweisungen.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Hinzufügen der `[Import]` -Attribut auf die Dienstschnittstelle wie folgt.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Wenn Sie den Dienst erhalten haben, können Sie eine der zugehörigen Komponenten nutzen.  
  
5.  Wenn Sie die Assembly, und fügen Sie ihn in kompiliert haben die... \Common7\IDE\Components\-Ordner der Visual Studio-Installation.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)