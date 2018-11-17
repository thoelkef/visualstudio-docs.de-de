---
title: Verfügbarmachen der Eigenschaften für das Fenster "Eigenschaften" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 026e7de7d56cb907682be52db2dbd32782822d9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756911"
---
# <a name="exposing-properties-to-the-properties-window"></a>Verfügbarmachen von Eigenschaften im Eigenschaftenfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise macht die öffentlichen Eigenschaften eines Objekts auf der **Eigenschaften** Fenster. Die Änderungen, die Sie, um diese Eigenschaften vornehmen werden angezeigt, der **Eigenschaften** Fenster.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Verfügbarmachen von Eigenschaften im Eigenschaftenfenster  
 In diesem Abschnitt können Sie auch ein benutzerdefiniertes Toolfenster zu erstellen und Anzeigen der öffentlichen Eigenschaften des Objekts im zugehörigen Fenster im Bereich der **Eigenschaften** Fenster.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Eigenschaften für das Fenster "Eigenschaften" verfügbar machen.  
  
1.  Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX-Projekt namens `MyObjectPropertiesExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster durch Hinzufügen eines benutzerdefinierten Toolfensters Elements einer Vorlage mit dem Namen `MyToolWindow`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **Dialogfeld "Neues Element hinzufügen"**, wechseln Sie zu **Visual c#-Elemente / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Toolfensters**. In der **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen an `MyToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  MyToolWindow.cs öffnen, und fügen Sie die folgenden using-Anweisung:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Fügen Sie jetzt die folgenden Felder mit den `MyToolWindow` Klasse.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Fügen Sie den folgenden Code, der MyToolWindow-Klasse.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Die `TrackSelection` Eigenschaft verwendet `GetService` zum Abrufen einer `STrackSelection` -Dienst, der bietet eine <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle. Die `OnToolWindowCreated` -Ereignishandler und `SelectList` Methode gemeinsam erstellen Sie eine Liste der ausgewählten Objekte, die nur der Bereich toolfensterobjekt selbst enthält. Die `UpdateSelection` Methode teilt dem **Eigenschaften** Fenster, um die öffentlichen Eigenschaften der Tool-Fensterbereich anzuzeigen.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7.  Wenn die **Eigenschaften** nicht sichtbar ist, öffnen Sie sie durch Drücken von F4.  
  
8.  Öffnen der **MyToolWindow** Fenster. Sie finden es im **anzeigen / Other Windows**.  
  
     Das Fenster wird geöffnet und die öffentlichen Eigenschaften des Fensterbereichs angezeigt, der **Eigenschaften** Fenster.  
  
9. Ändern der **Beschriftung** -Eigenschaft in der **Eigenschaften** Fenster **Meine Objekteigenschaften**.  
  
     Die fensterbeschriftung MyToolWindow ändert sich entsprechend.  
  
## <a name="exposing-tool-window-properties"></a>Verfügbarmachen von Eigenschaften der Tool-Fenster  
 In diesem Abschnitt fügen Sie ein Toolfenster und seine Eigenschaften verfügbar machen. Die Änderungen, die Sie, um die Eigenschaften vornehmen werden angezeigt, der **Eigenschaften** Fenster.  
  
#### <a name="to-expose-tool-window-properties"></a>Tool-Fenstereigenschaften verfügbar zu machen  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie die öffentliche boolesche Eigenschaft IsChecked, auf die MyToolWindow-Klasse.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Diese Eigenschaft ruft den Zustand ab, aus der WPF-Kontrollkästchen, das Sie später erstellen.  
  
2.  Öffnen Sie MyToolWindowControl.xaml.cs, und Ersetzen Sie den MyToolWindowControl-Konstruktor durch den folgenden Code.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Dadurch werden `MyToolWindowControl` Zugriff auf die `MyToolWindow` Bereich.  
  
3.  Ändern Sie im MyToolWindow.cs, die `MyToolWindow` Konstruktor wie folgt:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Ändern Sie in der Entwurfsansicht des MyToolWindowControl.  
  
5.  Die Schaltfläche "löschen", und fügen Sie das Kontrollkästchen aus der **Toolbox** auf der linken oberen Ecke.  
  
6.  Fügen Sie die Checked und Unchecked Ereignisse hinzu. Aktivieren Sie das Kontrollkästchen in der Entwurfsansicht. In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche "Ereignis-Handler" (oben rechts auf der die **Eigenschaften** Fenster). Suchen **Checked** , und geben **Checkbox_Checked** in das Textfeld, und suchen Sie dann **deaktiviert** und **Checkbox_Unchecked** in das Textfeld.  
  
7.  Fügen Sie die Kontrollkästchen-Ereignishandler hinzu:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
9. Öffnen Sie in der experimentellen Instanz den **MyToolWindow** Fenster.  
  
     Suchen Sie nach den Eigenschaften des Fensters, in der **Eigenschaften** Fenster. Die **IsChecked** Eigenschaft wird am unteren Fensterrand, unter dem **eigene Eigenschaften** Kategorie.  
  
10. Aktivieren Sie das Kontrollkästchen der **MyToolWindow** Fenster. **IsChecked** in die **Eigenschaften** wird daraufhin **"true"**. Deaktivieren Sie das Kontrollkästchen in der **MyToolWindow** Fenster. **IsChecked** in die **Eigenschaften** wird daraufhin **"false"**. Ändern Sie den Wert der **IsChecked** in die **Eigenschaften** Fenster. Das Kontrollkästchen in der **MyToolWindow** Fenster-Änderungen an den neuen Wert festlegen.  
  
    > [!NOTE]
    >  Wenn Sie ein Objekt zu verwerfen müssen, die in angezeigt wird der **Eigenschaften** Fenster, rufen `OnSelectChange` mit einem `null` Auswahlcontainer erste. Nach dem die Eigenschaft oder das Objekt verworfen wird, können Sie in einem Auswahlcontainer an, der aktualisiert wurde ändern <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> und <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> aufgeführt.  
  
## <a name="changing-selection-lists"></a>Ändern von Auswahllisten  
 In diesem Abschnitt fügen Sie eine Auswahlliste für eine grundlegende Eigenschaft-Klasse und Verwenden der Oberfläche des Tools auf der Auswahlliste angezeigt.  
  
#### <a name="to-change-selection-lists"></a>Ändern von Auswahllisten  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie eine öffentliche Klasse, die mit dem Namen `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Fügen Sie eine SimpleObject-Eigenschaft auf die Klasse MyToolWindow sowie zwei Methoden zum Wechseln der **Eigenschaften** Fenster-Auswahl zwischen den Fensterbereich und `Simple` Objekt.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  Ersetzen Sie in "mytoolwindowcontrol.cs" die Handler für das Kontrollkästchen mit diesen Codezeilen ein:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  Öffnen Sie in der experimentellen Instanz den **MyToolWindow** Fenster.  
  
6.  Wählen Sie das Kontrollkästchen in der **MyToolWindow** Fenster. Die **Eigenschaften** Fenster zeigt die `Simple` Objekteigenschaften, **Irgendein_text** und **ReadOnly**. Deaktivieren Sie das Kontrollkästchen. Die öffentlichen Eigenschaften des Fensters angezeigt wird, der **Eigenschaften** Fenster.  
  
    > [!NOTE]
    >  Der Anzeigename des **Irgendein_text** ist **My Text**.  
  
## <a name="best-practice"></a>Es wird empfohlen  
 In dieser exemplarischen Vorgehensweise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird implementiert, damit die Auflistung der auswählbaren Objekte und die ausgewählte Objekt-Sammlung derselben Sammlung sind. Nur das ausgewählte Objekt wird in der Liste der Eigenschaften-Browser angezeigt. Eine umfassendere ISelectionContainer-Implementierung finden Sie unter den Beispielen Reference.ToolWindow.  
  
 Visual Studio-Toolfenster bleiben zwischen Visual Studio-Sitzungen. Weitere Informationen zum Beibehalten des Zustands der Tool-Fenster, finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)

