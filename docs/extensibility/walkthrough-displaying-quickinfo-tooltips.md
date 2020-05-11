---
title: 'Exemplarische Vorgehensweise: Anzeigen von QuickInfo-Tooltips | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697440"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: QuickInfo-Tooltips anzeigen
QuickInfo ist eine IntelliSense-Funktion, die Methodensignaturen und Beschreibungen anzeigt, wenn ein Benutzer den Zeiger über einen Methodennamen bewegt. Sie können sprachbasierte Features wie QuickInfo implementieren, indem Sie die Bezeichner definieren, für die Sie QuickInfo-Beschreibungen bereitstellen möchten, und dann eine QuickInfo-Adresse erstellen, in der der Inhalt angezeigt werden soll. Sie können QuickInfo im Kontext eines Sprachdienstes definieren, oder Sie können Ihre eigene Dateinamenerweiterung und Ihren Inhaltstyp definieren und QuickInfo für genau diesen Typ anzeigen, oder Sie können QuickInfo für einen vorhandenen Inhaltstyp anzeigen (z. B. "Text"). In dieser exemplarischen Vorgehensweise wird gezeigt, wie QuickInfo für den Inhaltstyp "Text" angezeigt wird.

 Im QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise werden die Quicktips angezeigt, wenn ein Benutzer den Zeiger über einen Methodennamen bewegt. Für diesen Entwurf müssen Sie diese vier Schnittstellen implementieren:

- Quellschnittstelle

- Quellanbieterschnittstelle

- Controller-Schnittstelle

- Controller-Provider-Schnittstelle

  Die Quell- und Controlleranbieter sind MEF-Komponenten (Managed Extensibility Framework) und sind für den Export der <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Quell- und Controllerklassen sowie für <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>das Importieren von Diensten und Brokern verantwortlich, z. B. den , der den QuickTip-Textpuffer erstellt, und den , der die QuickInfo-Sitzung auslöst.

  In diesem Beispiel verwendet die QuickInfo-Quelle eine hartcodierte Liste von Methodennamen und Beschreibungen, aber in vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 müssen Sie das Visual Studio SDK nicht aus dem Downloadcenter installieren. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `QuickInfoTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-the-quickinfo-source"></a>Implementieren der QuickInfo-Quelle
 Die QuickInfo-Quelle ist für das Sammeln des Satzes von Bezeichnern und deren Beschreibungen und das Hinzufügen des Inhalts zum Quicktip-Textpuffer verantwortlich, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die Bezeichner und ihre Beschreibungen nur im Quellkonstruktor hinzugefügt.

#### <a name="to-implement-the-quickinfo-source"></a>So implementieren Sie die QuickInfo-Quelle

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.

2. Fügen Sie einen Verweis auf *Microsoft.VisualStudio.Language.IntelliSense*hinzu.

3. Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklarieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>eine Klasse, `TestQuickInfoSource`die implementiert, und benennen Sie sie .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Fügen Sie Felder für den QuickInfo-Quellanbieter, den Textpuffer und einen Satz von Methodennamen und Methodensignaturen hinzu. In diesem Beispiel werden die Methodennamen und `TestQuickInfoSource` Signaturen im Konstruktor initialisiert.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Fügen Sie einen Konstruktor hinzu, der den QuickInfo-Quellanbieter und den Textpuffer festlegt und den Satz von Methodennamen sowie Methodensignaturen und Beschreibungen auffüllt.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel findet die Methode das aktuelle Wort oder das vorherige Wort, wenn sich der Cursor am Ende einer Zeile oder eines Textpuffers befindet. Wenn das Wort einer der Methodennamen ist, wird die Beschreibung für diesen Methodennamen dem QuickInfo-Inhalt hinzugefügt.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Sie müssen auch eine Dispose()-Methode implementieren, da <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable>implementiert:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementieren eines QuickInfo-Quellanbieters
 Der Anbieter der QuickInfo-Quelle dient in erster Linie dazu, sich selbst als MEF-Komponententeil zu exportieren und die QuickInfo-Quelle zu instanziieren. Da es sich um ein MEF-Komponententeil handelt, kann es andere MEF-Komponenten importieren.

#### <a name="to-implement-a-quickinfo-source-provider"></a>So implementieren Sie einen QuickInfo-Quellanbieter

1. Deklarieren Sie einen `TestQuickInfoSourceProvider` QuickInfo-Quellanbieter mit dem Namen , <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>der implementiert, und exportieren Sie ihn mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "ToolTip QuickInfo Source", einem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von Before="default" und einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importieren Sie zwei <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Editordienste und `TestQuickInfoSourceProvider`als Eigenschaften von .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementieren, <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> um `TestQuickInfoSource`eine neue zurückzugeben.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementieren eines QuickInfo-Controllers
 QuickInfo-Controller bestimmen, wann QuickInfo angezeigt wird. In diesem Beispiel wird QuickInfo angezeigt, wenn sich der Zeiger über einem Wort befindet, das einem der Methodennamen entspricht. Der QuickInfo-Controller implementiert einen Maushover-Ereignishandler, der eine QuickInfo-Sitzung auslöst.

### <a name="to-implement-a-quickinfo-controller"></a>So implementieren Sie einen QuickInfo-Controller

1. Deklarieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>eine Klasse, `TestQuickInfoController`die implementiert, und benennen Sie sie .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Fügen Sie private Felder für die Textansicht, die in der Textansicht dargestellten Textpuffer, die QuickInfo-Sitzung und den QuickInfo-Controlleranbieter hinzu.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt und den Mauszeigerhover-Ereignishandler hinzufügt.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Fügen Sie den Maushover-Ereignishandler hinzu, der die QuickInfo-Sitzung auslöst.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Sie die Methode so, dass der Mauszeiger-Ereignishandler entfernt wird, wenn der Controller von der Textansicht getrennt wird.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode und die Methode als leere Methoden für dieses Beispiel.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des QuickInfo-Controlleranbieters
 Der Anbieter des QuickInfo-Controllers dient in erster Linie dazu, sich selbst als MEF-Komponententeil zu exportieren und den QuickInfo-Controller zu instanziieren. Da es sich um ein MEF-Komponententeil handelt, kann es andere MEF-Komponenten importieren.

### <a name="to-implement-the-quickinfo-controller-provider"></a>So implementieren Sie den QuickInfo-Controlleranbieter

1. Deklarieren `TestQuickInfoControllerProvider` Sie eine <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>Klasse mit dem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Namen , die implementiert, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> und exportieren Sie sie mit einem von "ToolTip QuickInfo Controller" und einem von "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Sie die Methode, indem Sie den QuickInfo-Controller instanziieren.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die QuickInfoTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>So erstellen und testen Sie die QuickInfoTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der die Wörter "add" und "subtract" enthält.

4. Bewegen Sie den Zeiger über eines der Vorkommen von "add". Die Signatur und die `add` Beschreibung der Methode sollten angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
