---
title: Managed Extensibility Framework im Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702869"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework im Editor
Der Editor wird mithilfe von MEF-Komponenten (Managed Extensibility Framework) erstellt. Sie können eigene MEF-Komponenten erstellen, um den Editor zu erweitern, und Ihr Code kann auch Editorkomponenten verwenden.

## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über das Managed Extensibility Framework
 Die MEF ist eine .NET-Bibliothek, mit der Sie Features einer Anwendung oder Komponente hinzufügen und ändern können, die dem MEF-Programmiermodell folgt. Der Visual Studio-Editor kann MEF-Komponenten bereitstellen und nutzen.

 Das MEF ist in der Assembly .NET Framework Version 4 *System.ComponentModel.Composition.dll* enthalten.

 Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Komponenten und Zusammensetzungsbehälter
 Ein Komponententeil ist eine Klasse oder ein Member einer Klasse, die eine (oder beide) der folgenden Schritte ausführen kann:

- Verwenden einer anderen Komponente

- Von einer anderen Komponente verbraucht werden

  Betrachten Sie beispielsweise eine Einkaufsanwendung mit einer Auftragserfassungskomponente, die von den Produktverfügbarkeitsdaten einer Lagerbestandskomponente abhängt. In MEF-Begriffen kann das Lagerteil Produktverfügbarkeitsdaten *exportieren,* und der Auftragseingangsteil kann die Daten *importieren.* Der Auftragseingangsteil und der Lagerteil müssen sich nicht kennen; Der *Kompositionscontainer* (der von der Hostanwendung bereitgestellt wird) ist für die Aufrechterhaltung des Satzes von Exporten und die Abwicklung der Exporte und Importe verantwortlich.

  Der Kompositionscontainer <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ist in der Regel im Besitz des Hosts. Der Kompositionscontainer verwaltet einen *Katalog* exportierter Komponententeile.

### <a name="export-and-import-component-parts"></a>Exportieren und Importieren von Komponenten
 Sie können jede Funktionalität exportieren, solange sie als öffentliche Klasse oder als öffentlicher Member einer Klasse (Eigenschaft oder Methode) implementiert ist. Sie müssen Ihr Komponententeil nicht <xref:System.ComponentModel.Composition.Primitives.ComposablePart>von ableiten. Stattdessen müssen Sie <xref:System.ComponentModel.Composition.ExportAttribute> der Klasse oder dem Klassenmember, die Sie exportieren möchten, ein Attribut hinzufügen. Dieses Attribut gibt den *Vertrag* an, mit dem ein anderes Komponententeil Ihre Funktionalität importieren kann.

### <a name="the-export-contract"></a>Der Exportvertrag
 Der <xref:System.ComponentModel.Composition.ExportAttribute> definiert die Entität (Klasse, Schnittstelle oder Struktur), die exportiert wird. In der Regel nimmt das Exportattribut einen Parameter an, der den Typ des Exports angibt.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Standardmäßig definiert <xref:System.ComponentModel.Composition.ExportAttribute> das Attribut einen Vertrag, der der Typ der Exportklasse ist.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Im Beispiel ist `[Export]` das Standardattribut `[Export(typeof(TestAdornmentLayerDefinition))]`äquivalent zu .

 Sie können auch eine Eigenschaft oder Methode exportieren, wie im folgenden Beispiel gezeigt.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importieren eines MEF-Exports
 Wenn Sie einen MEF-Export verwenden möchten, müssen Sie den Vertrag (in der <xref:System.ComponentModel.Composition.ImportAttribute> Regel den Typ) kennen, nach dem er exportiert wurde, und ein Attribut mit diesem Wert hinzufügen. Standardmäßig nimmt das import-Attribut einen Parameter an, der der Typ der Klasse ist, die es ändert. Die folgenden Codezeilen <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> importieren den Typ.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Abrufen der Editor-Funktionalität aus einem MEF-Komponententeil
 Wenn ihr vorhandener Code ein MEF-Komponententeil ist, können Sie MEF-Metadaten verwenden, um Editorkomponententeile zu verwenden.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>So nutzen Sie die Editorfunktionalität aus einem MEF-Komponententeil

1. Fügen Sie Verweise auf *System.Composition.ComponentModel.dll*, das sich im globalen Assemblycache (GAC) befindet, und zu den Editorassemblys hinzu.

2. Fügen Sie die entsprechenden Verwendungsdirektiven hinzu.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Fügen `[Import]` Sie das Attribut wie folgt zur Dienstschnittstelle hinzu.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Wenn Sie den Dienst erhalten haben, können Sie eine der Komponenten verwenden.

5. Wenn Sie ihre Assembly kompiliert haben, legen Sie sie in *.. Der Ordner "Common7-IDE-Komponenten"\* Ihrer Visual Studio-Installation.

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
