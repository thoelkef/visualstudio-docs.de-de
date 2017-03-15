---
title: "Verf&#252;gbarmachen von Eigenschaften im Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaften [Visual Studio SDK] im Eigenschaftenbrowser verfügbar machen"
  - "Eigenschaften [Visual Studio SDK]"
  - "Eigenschaftenbrowser, Verfügbarmachen von Eigenschaften"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Verf&#252;gbarmachen von Eigenschaften im Eigenschaftenfenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise macht die öffentlichen Eigenschaften eines Objekts, das **Eigenschaften** Fenster. Die Änderungen, die Sie, um diese Eigenschaften vornehmen werden angezeigt, der **Eigenschaften** Fenster.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Verfügbarmachen von Eigenschaften im Eigenschaftenfenster  
 In diesem Abschnitt erstellen Sie ein benutzerdefiniertes Toolfenster und Anzeigen der öffentlichen Eigenschaften des zugeordneten Fensters Pane\-Objekts in der **Eigenschaften** Fenster.  
  
#### Eigenschaften, um das Fenster Eigenschaften verfügbar machen.  
  
1.  Alle Visual Studio\-Erweiterung beginnt mit der ein VSIX\-Bereitstellungsprojekt, das die Ressourcen für die Erweiterung enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX\-Projekt namens `MyObjectPropertiesExtension`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster hinzu, indem Sie ein benutzerdefiniertes Toolfenster\-Elementvorlage mit dem Namen `MyToolWindow`. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Dialogfeld Neues Element hinzufügen**, zur **Visual C\#\-Elemente \/ Erweiterbarkeit** und wählen Sie **benutzerdefinierte Toolfenster**. In den **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen `MyToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Öffnen Sie MyToolWindow.cs, und fügen Sie die folgenden using\-Anweisung:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Fügen Sie jetzt die folgenden Felder zu den `MyToolWindow` Klasse.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Fügen Sie den folgenden Code zur MyToolWindow\-Klasse.  
  
    ```c#  
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
  
     Die `TrackSelection` \-Eigenschaft verwendet `GetService` Abrufen einer `STrackSelection` Service bietet eine <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle. Der `OnToolWindowCreated` \-Ereignishandler und `SelectList` \-Methode erstellen eine Liste der ausgewählten Objekte, die nur das Tool Bereich Fensterobjekt selbst enthält. Die `UpdateSelection` Methode teilt dem **Eigenschaften** die öffentlichen Eigenschaften des Toolbereichs im Fenster angezeigt werden soll.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7.  Wenn die **Eigenschaften** nicht sichtbar ist, öffnen Sie es durch Drücken von F4.  
  
8.  Öffnen Sie die **MyToolWindow** Fenster. Sie finden es in **Anzeigen \/ andere Fenster**.  
  
     Das Fenster wird geöffnet und die öffentlichen Eigenschaften Fensterbereich angezeigt werden, der **Eigenschaften** Fenster.  
  
9. Ändern der **Beschriftung** Eigenschaft in der **Eigenschaften** Fenster **Meine Objekteigenschaften**.  
  
     Die MyToolWindow Fenstertitel ändert sich entsprechend.  
  
## Verfügbarmachen von Eigenschaften der Tool\-Fenster  
 In diesem Abschnitt fügen Sie ein Toolfenster und seine Eigenschaften verfügbar machen. Die Änderungen an Eigenschaften werden angezeigt, der **Eigenschaften** Fenster.  
  
#### Tools im Fenstereigenschaften verfügbar machen  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie die öffentliche boolesche Eigenschaft IsChecked zur MyToolWindow\-Klasse.  
  
    ```c#  
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
  
     Diese Eigenschaft ruft den Zustand ab, aus dem WPF\-Kontrollkästchen, das Sie später erstellen.  
  
2.  Öffnen Sie MyToolWindowControl.xaml.cs, und Ersetzen Sie den MyToolWindowControl\-Konstruktor durch den folgenden Code.  
  
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
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Ändern Sie in der Entwurfsansicht des MyToolWindowControl.  
  
5.  Die Schaltfläche "löschen", und fügen Sie ein Kontrollkästchen aus der **Toolbox** in der linken oberen Ecke.  
  
6.  Checked und Unchecked\-Ereignisse hinzufügen. Aktivieren Sie das Kontrollkästchen in der Entwurfsansicht. In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche "Ereignis\-Handler" \(oben rechts auf der die **Eigenschaften** Fenster\). Suchen **aktiviert** und **Checkbox\_Checked** in das Textfeld Suchen **deaktiviert** und **Checkbox\_Unchecked** in das Textfeld.  
  
7.  Fügen Sie die Kontrollkästchen\-Ereignishandler hinzu:  
  
    ```c#  
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
  
     Suchen Sie das Fenster Eigenschaften für die **Eigenschaften** Fenster. Die **IsChecked** Eigenschaft wird am unteren Fensterrand, unter der **Eigenschaften meiner** Kategorie.  
  
10. Aktivieren Sie das Kontrollkästchen der **MyToolWindow** Fenster.**IsChecked** in der **Eigenschaften** wird daraufhin **True**. Deaktivieren Sie das Kontrollkästchen in der **MyToolWindow** Fenster.**IsChecked** in der **Eigenschaften** wird daraufhin **False**. Ändern Sie den Wert der **IsChecked** in der **Eigenschaften** Fenster. Das Kontrollkästchen in der **MyToolWindow** Fenster Änderungen mit dem neuen Wert übereinstimmen.  
  
    > [!NOTE]
    >  Wenn Sie ein Objekt freigeben müssen, die in angezeigt wird der **Eigenschaften** Fenster, rufen Sie `OnSelectChange` mit einer `null` Auswahlcontainer erste. Nach entfernen die Eigenschaft oder das Objekt, können Sie in einer Auswahlcontainer, der aktualisiert wurde, ändern, <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> und <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> aufgeführt.  
  
## Ändern von Auswahllisten  
 In diesem Abschnitt fügen Sie eine Auswahlliste für eine grundlegende Eigenschaftsklasse und Verwenden der Oberfläche des Tools die Auswahlliste anzeigen auswählen.  
  
#### Ändern von Auswahllisten  
  
1.  Öffnen Sie MyToolWindow.cs, und fügen Sie eine öffentliche Klasse mit dem Namen `Simple`.  
  
    ```c#  
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
  
2.  Hinzufügen einer SimpleObject\-Eigenschaft der Klasse MyToolWindow plus zwei Methoden zum Wechseln der **Eigenschaften** eine Auswahl zwischen dem Fensterbereich und `Simple` Objekt.  
  
    ```c#  
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
  
3.  Ersetzen Sie in MyToolWindowControl.cs die Handler für das Kontrollkästchen mit den folgenden Codezeilen:  
  
    ```c#  
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
  
6.  Aktivieren Sie das Kontrollkästchen in der **MyToolWindow** Fenster. Die **Eigenschaften** Fenster zeigt die `Simple` Objekteigenschaften, **SomeText** und **ReadOnly**. Deaktivieren Sie das Kontrollkästchen. Die öffentlichen Eigenschaften des Fensters angezeigt wird, der **Eigenschaften** Fenster.  
  
    > [!NOTE]
    >  Der Anzeigename des **SomeText** ist **Mein Text**.  
  
## Es wird empfohlen  
 In dieser exemplarischen Vorgehensweise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ist implementiert, damit die Auflistung auswählbare Objekt und der Auflistung ausgewählten Objekt dieselbe Auflistung sind. Nur das ausgewählte Objekt wird in den Eigenschaftenbrowser angezeigt. Eine umfassendere ISelectionContainer Implementierung finden Sie unter der Reference.ToolWindow Beispiele.  
  
 Visual Studio\-Toolfenster, die zwischen den Visual Studio\-Sitzungen beibehalten werden. Weitere Informationen zum Beibehalten des Zustands der Tool\-Fenster, finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Siehe auch  
 [Erweitern von Eigenschaften und das Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md)