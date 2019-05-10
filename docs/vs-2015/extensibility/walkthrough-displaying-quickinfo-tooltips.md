---
title: 'Exemplarische Vorgehensweise: Anzeigen von QuickInfos | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79ce531d36b21ab26cf4c6e6dc76e8c4d98d8763
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960040"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: Anzeigen von QuickInfos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo wird eine IntelliSense-Funktion, die Methodensignaturen anzeigt und Beschreibungen, wenn ein Benutzer den Mauszeiger über einen Methodennamen. Sie können die Sprache basierenden Features wie QuickInfo implementieren, definieren die Bezeichner für die Sie die QuickInfo-Beschreibungen bereitstellen möchten, und erstellen dann eine QuickInfo, in dem den Inhalt angezeigt. Sie können die QuickInfo im Kontext von einem Sprachdienst definieren oder können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateinamentyp und Anzeigen der QuickInfo für nur diesen Typ, oder Sie können die QuickInfo anzeigen, für die einem vorhandenen Inhaltstyp (z. B. "Text"). Dieser exemplarischen Vorgehensweise beim Anzeigen von QuickInfos für den Inhaltstyp "Text".  
  
 Das QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise zeigt die QuickInfo an, wenn ein Benutzer den Zeiger über einen Methodennamen. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:  
  
- Source-Schnittstelle  
  
- Anbieterschnittstelle für die Quelle  
  
- Controller-Schnittstelle  
  
- Controller-Provider-Schnittstelle  
  
  Die Quell- und Controller-Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind verantwortlich für die Quell- und Controller-Klassen exportieren und importieren und z. B.-Broker die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, die den QuickInfo-Text erstellt Puffer, und die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, der die QuickInfo-Sitzung ausgelöst.  
  
  In diesem Beispiel die QuickInfo-Quelle verwendet eine hartcodierte Liste mit Namen und Beschreibungen, aber in vollständige Implementierungen der Sprachdienst und der zugehörigen Dokumentation sind dafür verantwortlich, dass der Inhalt.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual C# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `QuickInfoTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementieren der QuickInfo-Quelle  
 Die QuickInfo-Quelle ist verantwortlich für das Sammeln des Satz von IDs und Beschreibungen, und den Inhalt auf den QuickInfo-Text-Puffer hinzugefügt werden, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die IDs und Beschreibungen nur in den Konstruktor des Quelle hinzugefügt.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Um die QuickInfo-Quelle zu implementieren.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Language.IntelliSense hinzu.  
  
3.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, und nennen Sie sie `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Hinzufügen von Feldern für der Quellenanbieter QuickInfos, das den Textpuffer und einen Satz von Namen und Signaturen. In diesem Beispiel den Namen und Signaturen werden initialisiert die `TestQuickInfoSource` Konstruktor.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Fügen Sie einen Konstruktor, der festlegt, der Quellenanbieter QuickInfo und den Textpuffer und füllt die Gruppe von Methoden und Signaturen und Beschreibungen.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel sucht die Methode das aktuelle Wort oder vorherigen Wort, wenn der Cursor befindet sich am Ende einer Zeile oder einen Textpuffer. Wenn das Wort auf eine der Methode handelt, wird die Beschreibung dieser Methodenname der QuickInfo-Inhalt hinzugefügt.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  Sie müssen auch eine Dispose()-Methode implementieren, da <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementieren eines Anbieters für die QuickInfo-Quelle  
 Der Anbieter, der den QuickInfo-Quelle dient in erster Linie zum Exportieren von sich selbst als einer MEF-Komponente und die QuickInfo-Quelle zu instanziieren. Da es sich um einen MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementierung eines Anbieters der QuickInfo-Quelle  
  
1.  Deklarieren einen QuickInfo-Source-Anbieter mit dem Namen `TestQuickInfoSourceProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo QuickInfo Source" eine <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default", und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  Importieren von zwei Editor Dienste <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, als Eigenschaften des `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> zurückzugebenden ein neues `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementieren eine QuickInfo-Controller  
 QuickInfo-Controller bestimmen, wenn QuickInfos angezeigt werden soll. In diesem Beispiel wird die QuickInfo angezeigt, wenn der Zeiger über ein Wort, das eine der Methode entspricht, wird. Der QuickInfo-Controller implementiert einen Mausereignishandler gezeigt wird, der eine QuickInfo-Sitzung ausgelöst.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Um ein QuickInfo-Controller zu implementieren.  
  
1.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, und nennen Sie sie `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Fügen Sie private Felder für die Textansicht, das die Textpuffer dargestellt, in der Textansicht, die QuickInfo-Sitzung und der QuickInfo-Controller-Anbieter hinzu.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Fügen Sie einen Konstruktor, der die Felder festgelegt, und fügt den Ereignishandler der Maus gezeigt wird.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Fügen Sie den Maus zeigen Sie Ereignishandler, der die QuickInfo-Sitzung auslöst.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode, sodass die It den Ereignishandler der Maus gezeigt wird entfernt, wenn der Controller von der Textansicht getrennt wird.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> Methode und die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des QuickInfo-Controller-Anbieters  
 Der Anbieter, der den QuickInfo-Controller dient in erster Linie zum Exportieren von sich selbst als einer MEF-Komponente, und instanziieren Sie den QuickInfo-Controller. Da es sich um einen MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Den QuickInfo-Controller-Anbieter implementiert  
  
1.  Deklarieren Sie eine Klasse, die mit dem Namen `TestQuickInfoControllerProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo-QuickInfo-Controllers" und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  Importieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode durch die Instanziierung des QuickInfo-Controllers.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe QuickInfoTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Zum Erstellen und Testen der Lösung QuickInfoTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und Typ, der die Wörter enthält Text "hinzufügen" und "subtrahieren".  
  
4.  Zeigen Sie auf ein Vorkommen von "hinzufügen". Die Signatur und die Beschreibung der `add` Methode angezeigt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
