---
title: Managed Extensibility Framework im Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f19b71c86d972b59a9d46f379bf7ec93f63aeb9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679959"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework im Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Editor wird mithilfe von Managed Extensibility Framework-Komponenten (MEF) erstellt. Sie können Ihre eigenen MEF-Komponenten erstellen, um den Editor zu erweitern, und der Code kann auch Editor-Komponenten nutzen.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über den Managed Extensibility Framework  
 Die MEF ist eine .NET-Bibliothek, mit der Sie Features einer Anwendung oder Komponente hinzufügen und ändern können, die dem MEF-Programmiermodell folgt. Der Visual Studio-Editor kann MEF-Komponenten Teile bereitstellen und nutzen.  
  
 Die MEF ist in der .NET Framework Version 4 System.ComponentModel.Composition.dll Assembly enthalten.  
  
 Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Komponenten Teile und Kompositions Container  
 Ein Komponenten Teil ist eine Klasse oder ein Member einer Klasse, die eine (oder beide) der folgenden Aktionen ausführen kann:  
  
- Verwenden einer anderen Komponente  
  
- Von einer anderen Komponente genutzt werden  
  
  Stellen Sie sich z. b. eine Einkaufs Anwendung vor, die über eine Bestell Eingabe Komponente verfügt, die von Produkt Verfügbarkeitsdaten abhängt, die von einer Warehouse-Bestands Komponente In MEF-Begriffen kann der Inventur Teil Produkt Verfügbarkeitsdaten *exportieren* , und der Bestell Eintrags Teil kann die Daten *importieren* . Der Bestell Eintrags Teil und der Inventur Teil müssen sich nicht gegenseitig informieren. der *Kompositions Container* (der von der Host Anwendung bereitgestellt wird) ist dafür verantwortlich, den Export Satz zu verwalten und die Exporte und Importe zu beheben.  
  
  Der Kompositions Container, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> , befindet sich in der Regel im Besitz des Hosts. Der Kompositions Container verwaltet einen *Katalog* exportierter Komponenten Teile.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportieren und Importieren von Komponenten teilen  
 Sie können jede beliebige Funktionalität exportieren, sofern Sie als öffentliche Klasse oder als öffentliches Member einer Klasse (Eigenschaft oder Methode) implementiert ist. Sie müssen den Komponenten Teil nicht von ableiten <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Stattdessen müssen Sie <xref:System.ComponentModel.Composition.ExportAttribute> der Klasse oder dem Klassenmember, die Sie exportieren möchten, ein-Attribut hinzufügen. Dieses Attribut gibt den *Vertrag* an, mit dem ein anderer Komponenten Teil ihre Funktionalität importieren kann.  
  
### <a name="the-export-contract"></a>Der Export Vertrag  
 <xref:System.ComponentModel.Composition.ExportAttribute>Definiert die Entität (Klasse, Schnittstelle oder Struktur), die exportiert wird. In der Regel nimmt das Export-Attribut einen Parameter an, der den Typ des Exports angibt.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Standardmäßig definiert das- <xref:System.ComponentModel.Composition.ExportAttribute> Attribut einen Vertrag, bei dem es sich um den Typ der exportierenden Klasse handelt.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Im Beispiel entspricht das Default- `[Export]` Attribut `[Export(typeof(TestAdornmentLayerDefinition))]` .  
  
 Sie können auch eine Eigenschaft oder Methode exportieren, wie im folgenden Beispiel gezeigt.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importieren eines MEF-Exports  
 Wenn Sie einen MEF-Export nutzen möchten, müssen Sie den-Vertrag (in der Regel den-Typ) kennen, mit dem er exportiert wurde, und ein- <xref:System.ComponentModel.Composition.ImportAttribute> Attribut mit diesem Wert hinzufügen. Standardmäßig nimmt das Import-Attribut einen Parameter an, der der Typ der Klasse ist, den er ändert. In den folgenden Codezeilen wird der- <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Typ importiert.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Erhalten von Editor-Funktionen aus einem MEF-Komponenten Teil  
 Wenn Ihr vorhandener Code ein MEF-Komponenten Teil ist, können Sie die MEF-Metadaten verwenden, um editorkomponententeile zu verwenden.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>So nutzen Sie die Editor-Funktionalität von einem MEF-Komponenten Teil  
  
1. Fügen Sie Verweise auf System.Composition.ComponentModel.dll im globalen Assemblycache (Global Assembly Cache, GAC) und auf die editorassemblys hinzu.  
  
2. Fügen Sie die relevanten using-Anweisungen hinzu.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. Fügen Sie das- `[Import]` Attribut wie folgt zu ihrer Dienst Schnittstelle hinzu.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. Wenn Sie den Dienst erhalten haben, können Sie eine beliebige Komponente nutzen.  
  
5. Wenn Sie die Assembly kompiliert haben, platzieren Sie Sie in. Ordner \common7\ide\components\ Ihrer Visual Studio-Installation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)
