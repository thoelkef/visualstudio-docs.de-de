---
title: "Exemplarische Vorgehensweise: Anzeigen von QuickInfos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neue - QuickInfo"
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Anzeigen von QuickInfos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

QuickInfo ist ein IntelliSense\-Feature, die Methodensignaturen anzeigt und eine Beschreibung, wenn ein Benutzer den Mauszeiger über einen Methodennamen. Sie können\-basierter Funktionen wie QuickInfo implementieren, definieren die Bezeichner für die Sie QuickInfo\-Beschreibung bereitstellen möchten, und erstellen eine QuickInfo an, in dem den Inhalt angezeigt. Können Sie QuickInfo im Kontext eines Dienstes Sprache definieren können eigene Erweiterung und Inhalt Dateinamentyp definieren und Anzeigen der QuickInfo für nur diesen Typ oder QuickInfo für einen vorhandenen Inhaltstyp \(z. B. "Text"\) anzuzeigen. Diese exemplarische Vorgehensweise veranschaulicht, wie QuickInfo für den Inhaltstyp "Text" angezeigt wird.  
  
 Die QuickInfo wird in dieser exemplarischen Vorgehensweise zeigt die QuickInfos, wenn ein Benutzer den Mauszeiger über einen Methodennamen bewegt. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:  
  
-   Source\-Schnittstelle  
  
-   Provider\-Schnittstelle  
  
-   Controller\-Schnittstelle  
  
-   Provider\-Schnittstelle  
  
 Die Quell\- und Controller\-Anbieter sind Managed Extensibility Framework \(MEF\)\-Komponenten und verantwortlich für die Quell\- und Controller\-Klassen exportieren und importieren und handelt, z. B. die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, der den QuickInfo\-Text\-Puffer erstellt und die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, dadurch wird die QuickInfo\-Sitzung ausgelöst.  
  
 In diesem Beispiel wird die QuickInfo\-Quelle verwendet eine hartcodierte Liste mit Namen und Beschreibungen, aber vollständige Implementierung der Sprachdienst und in der sprachdokumentation sind dafür verantwortlich, dass der Inhalt.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
#### So erstellen Sie ein MEF\-Projekt  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `QuickInfoTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## Implementieren der QuickInfo\-Quelle  
 Die QuickInfo\-Quelle ist verantwortlich für das Sammeln der Satz von Bezeichnern und deren Beschreibung und den Inhalt in den QuickInfo\-Text\-Puffer hinzufügen, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die Bezeichner und Beschreibungen nur im Konstruktor Quelle hinzugefügt.  
  
#### Implementieren Sie die QuickInfo\-Quelle  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `TestQuickInfoSource`.  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-cs[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, und nennen Sie es `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-cs[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Hinzufügen von Feldern für die QuickInfo Quellenanbieter Textpuffer und eine Reihe von Namen und Signaturen. In diesem Beispiel den Namen und Signaturen initialisiert werden die `TestQuickInfoSource` Konstruktor.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-cs[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Fügen Sie einen Konstruktor, der den QuickInfo\-Quellenanbieter und Textpuffer und den Satz von Methoden und Methodensignaturen und eine Beschreibung füllt hinzu.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-cs[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>\-Methode. In diesem Beispiel sucht die Methode das aktuelle Wort oder vorherigen Wort, wenn der Cursor am Ende einer Zeile oder einem Textpuffer ist. Wenn das Wort einen der Methode angegeben ist, wird die Beschreibung dieser Methodenname der QuickInfo\-Inhalt hinzugefügt.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-cs[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Sie müssen auch eine Dispose\(\)\-Methode implementieren, da <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-cs[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## Implementieren eines Anbieters für die QuickInfo\-Quelle  
 Der Anbieter der QuickInfo Quelle dient in erster Linie, exportieren selbst als Teil einer MEF\-Komponente und die QuickInfo\-Quelle instanziieren. Da es sich um eine MEF\-Komponente handelt, können sie andere Teile der MEF\-Komponente importieren.  
  
#### Implementierung eines Anbieters der QuickInfo\-Quelle  
  
1.  Deklarieren Sie eine QuickInfo Quellenanbieter mit dem Namen `TestQuickInfoSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "ToolTip QuickInfo Quelle" eine <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor \= "Default", und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-cs[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importieren von zwei Editor\-Dienste, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, als Eigenschaften des `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-cs[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> zurückzugebenden ein neues `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-cs[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## Implementieren eine QuickInfo\-Controller  
 QuickInfo\-Controller bestimmen, wann die QuickInfo angezeigt werden soll. In diesem Beispiel wird die QuickInfo angezeigt, wenn der Mauszeiger über ein Wort ist, die den Methodennamen entspricht. Der QuickInfo\-Controller implementiert einen Mausereignishandler gezeigt wird, der eine QuickInfo\-Sitzung auslöst.  
  
#### Implementieren Sie einen QuickInfo\-controller  
  
1.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, und nennen Sie es `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-cs[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Fügen Sie private Felder für die Textansicht die Textpuffer in der Textansicht, die QuickInfo\-Sitzung und die QuickInfo\-Controller\-Anbieter dargestellt.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-cs[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Fügen Sie einen Konstruktor, der die Felder festgelegt und fügt den Ereignishandler der Maus gezeigt wird.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-cs[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Fügen Sie den Mausereignishandler gezeigt wird hinzu, der die QuickInfo\-Sitzung auslöst.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-cs[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode so, dass die It Hover Mausereignishandler entfernt, wenn der Controller von der Textansicht getrennt wird.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-cs[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> \-Methode und der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-cs[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## Implementieren des QuickInfo\-Controller\-Anbieters  
 Der Anbieter des Controllers QuickInfo dient in erster Linie auf sich selbst als eine MEF\-Komponente exportiert und instanziieren Sie den QuickInfo\-Controller. Da es sich um eine MEF\-Komponente handelt, können sie andere Teile der MEF\-Komponente importieren.  
  
#### Den QuickInfo\-Controller\-Anbieter implementiert  
  
1.  Deklarieren Sie eine Klasse mit dem Namen `TestQuickInfoControllerProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von 'QuickInfo\-QuickInfo\-Controller' und einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-cs[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-cs[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode durch die Instanziierung des QuickInfo\-Controllers.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-cs[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe QuickInfoTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung QuickInfoTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und geben Sie Text an, der das Wort "hinzufügen" und "subtrahieren".  
  
4.  Den Mauszeiger über ein Vorkommen von "hinzufügen". Die Signatur und die Beschreibung der `add` Methode angezeigt werden soll.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)