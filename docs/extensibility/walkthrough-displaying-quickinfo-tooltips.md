---
title: 'Exemplarische Vorgehensweise: Anzeigen von QuickInfos | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6939ed93a07ab8a51de4fde6a5b063a586dc26de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713268"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: Anzeigen von QuickInfos
QuickInfo wird eine IntelliSense-Funktion, die Methodensignaturen anzeigt und Beschreibungen, wenn ein Benutzer den Mauszeiger über einen Methodennamen. Sie können die Sprache basierenden Features wie QuickInfo implementieren, definieren die Bezeichner für die Sie die QuickInfo-Beschreibungen bereitstellen möchten, und erstellen dann eine QuickInfo, in dem den Inhalt angezeigt. Sie können die QuickInfo im Kontext von einem Sprachdienst definieren oder können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateinamentyp und Anzeigen der QuickInfo für nur diesen Typ, oder Sie können die QuickInfo anzeigen, für die einem vorhandenen Inhaltstyp (z. B. "Text"). Dieser exemplarischen Vorgehensweise beim Anzeigen von QuickInfos für den Inhaltstyp "Text".

 Das QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise zeigt die QuickInfo an, wenn ein Benutzer den Zeiger über einen Methodennamen. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:

- Source-Schnittstelle

- Anbieterschnittstelle für die Quelle

- Controller-Schnittstelle

- Controller-Provider-Schnittstelle

  Die Quell- und Controller-Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind verantwortlich für die Quell- und Controller-Klassen exportieren und importieren und z. B.-Broker die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, die den QuickInfo-Text erstellt Puffer, und die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, der die QuickInfo-Sitzung ausgelöst.

  In diesem Beispiel die QuickInfo-Quelle verwendet eine hartcodierte Liste mit Namen und Beschreibungen, aber in vollständige Implementierungen der Sprachdienst und der zugehörigen Dokumentation sind dafür verantwortlich, dass der Inhalt.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, müssen Sie die Visual Studio-SDK aus dem Downloadcenter installieren. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `QuickInfoTest`.

2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-the-quickinfo-source"></a>Implementieren Sie die QuickInfo-Quelle
 Die QuickInfo-Quelle ist verantwortlich für das Sammeln des Satz von IDs und Beschreibungen, und den Inhalt auf den QuickInfo-Text-Puffer hinzugefügt werden, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die IDs und Beschreibungen nur in den Konstruktor des Quelle hinzugefügt.

#### <a name="to-implement-the-quickinfo-source"></a>Um die QuickInfo-Quelle zu implementieren.

1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.

2.  Hinzufügen eines Verweises auf *Microsoft.VisualStudio.Language.IntelliSense*.

3.  Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, und nennen Sie sie `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5.  Hinzufügen von Feldern für der Quellenanbieter QuickInfos, das den Textpuffer und einen Satz von Namen und Signaturen. In diesem Beispiel den Namen und Signaturen werden initialisiert die `TestQuickInfoSource` Konstruktor.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6.  Fügen Sie einen Konstruktor, der festlegt, der Quellenanbieter QuickInfo und den Textpuffer und füllt die Gruppe von Methoden und Signaturen und Beschreibungen.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel sucht die Methode das aktuelle Wort oder vorherigen Wort, wenn der Cursor befindet sich am Ende einer Zeile oder einen Textpuffer. Wenn das Wort auf eine der Methode handelt, wird die Beschreibung dieser Methodenname der QuickInfo-Inhalt hinzugefügt.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8.  Sie müssen auch eine Dispose()-Methode implementieren, da <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementieren eines Anbieters der QuickInfo-Quelle
 Der Anbieter, der den QuickInfo-Quelle dient in erster Linie zum Exportieren von sich selbst als einer MEF-Komponente und die QuickInfo-Quelle zu instanziieren. Da es sich um einen MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementierung eines Anbieters der QuickInfo-Quelle

1.  Deklarieren einen QuickInfo-Source-Anbieter mit dem Namen `TestQuickInfoSourceProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo QuickInfo Source" eine <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default", und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2.  Importieren von zwei Editor Dienste <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, als Eigenschaften des `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> zurückzugebenden ein neues `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementieren Sie einen QuickInfo-controller
 QuickInfo-Controller bestimmen, wenn die QuickInfo angezeigt wird. In diesem Beispiel wird QuickInfo angezeigt, wenn der Mauszeiger über ein Wort befindet, die eine der Methode entspricht. Der QuickInfo-Controller implementiert einen Mausereignishandler gezeigt wird, der eine QuickInfo-Sitzung ausgelöst.

### <a name="to-implement-a-quickinfo-controller"></a>Um ein QuickInfo-Controller zu implementieren.

1.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, und nennen Sie sie `TestQuickInfoController`.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2.  Fügen Sie private Felder für die Textansicht, das die Textpuffer dargestellt, in der Textansicht, die QuickInfo-Sitzung und der QuickInfo-Controller-Anbieter hinzu.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3.  Fügen Sie einen Konstruktor, der die Felder festgelegt, und fügt den Ereignishandler der Maus gezeigt wird.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4.  Fügen Sie den Maus zeigen Sie Ereignishandler, der die QuickInfo-Sitzung auslöst.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode, sodass die It den Ereignishandler der Maus gezeigt wird entfernt, wenn der Controller von der Textansicht getrennt wird.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> Methode und die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des QuickInfo-Controller-Anbieters
 Der Anbieter, der den QuickInfo-Controller dient in erster Linie zum Exportieren von sich selbst als einer MEF-Komponente, und instanziieren Sie den QuickInfo-Controller. Da es sich um einen MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Den QuickInfo-Controller-Anbieter implementiert

1.  Deklarieren Sie eine Klasse, die mit dem Namen `TestQuickInfoControllerProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo-QuickInfo-Controllers" und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2.  Importieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode durch die Instanziierung des QuickInfo-Controllers.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projektmappe QuickInfoTest, und führen Sie es in der experimentellen Instanz.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Zum Erstellen und Testen der Lösung QuickInfoTest

1.  Erstellen Sie die Projektmappe.

2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3.  Erstellen Sie eine Textdatei und Typ, der die Wörter enthält Text "hinzufügen" und "subtrahieren".

4.  Zeigen Sie auf ein Vorkommen von "hinzufügen". Die Signatur und die Beschreibung der `add` Methode angezeigt werden soll.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)