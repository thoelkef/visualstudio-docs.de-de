---
title: Eigenschaften für das Eigenschaftenfenster anzeigen | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711825"
---
# <a name="expose-properties-to-the-properties-window"></a>Verfügbar machen von Eigenschaften im Eigenschaftenfenster

In dieser exemplarischen Vorgehensweise werden die öffentlichen Eigenschaften eines Objekts für das **Eigenschaftenfenster** verfügbar gemacht. Die Änderungen, die Sie an diesen Eigenschaften vornehmen, werden im **Eigenschaftenfenster** widergespiegelt.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Verfügbar machen von Eigenschaften im Eigenschaftenfenster

In diesem Abschnitt erstellen Sie ein benutzerdefiniertes Toolfenster und zeigen die öffentlichen Eigenschaften des zugeordneten Fensterbereichsobjekts im **Eigenschaftenfenster** an.

### <a name="to-expose-properties-to-the-properties-window"></a>So machen Sie Eigenschaften für das Eigenschaftenfenster verfügbar

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungsprojekt, das die Erweiterungselemente enthält. Erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie ein `MyObjectPropertiesExtension`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Fügen Sie ein Toolfenster hinzu, indem `MyToolWindow`Sie eine elementemustergebundene Vorlage für das benutzerdefinierte Werkzeugfenster mit dem Namen hinzufügen. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im **Dialogfeld Neues Element hinzufügen**zu **Visual C-Items** > **Extensibility,** und wählen Sie **Benutzerdefiniertes Werkzeugfenster**aus. Ändern Sie im Feld **Name** am unteren Rand des Dialogfelds den Dateinamen in *MyToolWindow.cs*. Weitere Informationen zum Erstellen eines benutzerdefinierten Werkzeugfensters finden Sie unter [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Öffnen *Sie MyToolWindow.cs,* und fügen Sie die folgende Using-Anweisung hinzu:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Fügen Sie nun die `MyToolWindow` folgenden Felder zur Klasse hinzu.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Fügen Sie der `MyToolWindow` -Klasse den folgenden Code hinzu.

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

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    Die `TrackSelection` Eigenschaft `GetService` verwendet, `STrackSelection` um einen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Dienst abzuerhalten, der eine Schnittstelle bereitstellt. Der `OnToolWindowCreated` Ereignishandler `SelectList` und die Methode erstellen zusammen eine Liste ausgewählter Objekte, die nur das Werkzeugfensterfensterobjekt selbst enthält. Die `UpdateSelection` Methode weist das **Eigenschaftenfenster** an, die öffentlichen Eigenschaften des Werkzeugfensterbereichs anzuzeigen.

6. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

7. Wenn das **Eigenschaftenfenster** nicht sichtbar ist, öffnen Sie es, indem Sie **F4**drücken.

8. Öffnen Sie das **Fenster MyToolWindow.** Sie finden es in **View** > **Other Windows**.

    Das Fenster wird geöffnet, und die öffentlichen Eigenschaften des Fensterbereichs werden im **Eigenschaftenfenster** angezeigt.

9. Ändern Sie die **Caption-Eigenschaft** im **Eigenschaftenfenster** in **Meine Objekteigenschaften**.

     Die MyToolWindow-Fensterbeschriftung ändert sich entsprechend.

## <a name="expose-tool-window-properties"></a>Verfügbar machen von Werkzeugfenstereigenschaften

In diesem Abschnitt fügen Sie ein Toolfenster hinzu und machen dessen Eigenschaften verfügbar. Die Änderungen, die Sie an Eigenschaften vornehmen, werden im **Eigenschaftenfenster** widergespiegelt.

### <a name="to-expose-tool-window-properties"></a>So machen Sie Werkzeugfenstereigenschaften verfügbar

1. Öffnen *Sie MyToolWindow.cs*, und fügen Sie der `MyToolWindow` Klasse die öffentliche boolesche Eigenschaft IsChecked hinzu.

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

     Diese Eigenschaft erhält ihren Status aus dem WPF-Kontrollkästchen, das Sie später erstellen werden.

2. Öffnen *Sie MyToolWindowControl.xaml.cs* und ersetzen Sie den MyToolWindowControl-Konstruktor durch den folgenden Code.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Dadurch `MyToolWindowControl` wird der `MyToolWindow` Zugriff auf den Bereich ermöglicht.

3. Ändern *Sie*in `MyToolWindow` MyToolWindow.cs den Konstruktor wie folgt:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Ändern Sie die Entwurfsansicht von MyToolWindowControl.

5. Löschen Sie die Schaltfläche, und fügen Sie ein Kontrollkästchen aus der **Toolbox** zur oberen linken Ecke hinzu.

6. Fügen Sie die Ereignisse "Geprüft" und "Ungeprüft" hinzu. Aktivieren Sie das Kontrollkästchen in der Entwurfsansicht. Klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche Ereignishandler (oben rechts im **Eigenschaftenfenster).** Suchen Sie **überprüft,** und geben Sie **checkbox_Checked** in das Textfeld ein, und suchen Sie dann **nach Deaktiviert,** und geben Sie **checkbox_Unchecked** in das Textfeld ein.

7. Fügen Sie die Kontrollkästchen-Ereignishandler hinzu:

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

8. Erstellen Sie das Projekt, und starten Sie das Debugging.

9. Öffnen Sie in der experimentellen Instanz das **Fenster MyToolWindow.**

     Suchen Sie im **Eigenschaftenfenster** nach den Eigenschaften des Fensters. Die **IsChecked-Eigenschaft** wird am unteren Rand des Fensters unter der Kategorie **Meine Eigenschaften** angezeigt.

10. Aktivieren Sie das Kontrollkästchen im **Fenster MyToolWindow.** **IsChecked** im **Eigenschaftenfenster** ändert sich in **True**. Deaktivieren Sie das Kontrollkästchen im **Fenster MyToolWindow.** **IsChecked** im **Eigenschaftenfenster** ändert sich in **False**. Ändern Sie den Wert von **IsChecked** im **Eigenschaftenfenster.** Das Kontrollkästchen im **Fenster MyToolWindow** wird so geändert, dass es mit dem neuen Wert übereinstimmt.

    > [!NOTE]
    > Wenn Sie ein Objekt entsorgen müssen, das im `OnSelectChange` **Eigenschaftenfenster** angezeigt wird, rufen Sie zuerst mit einem `null` Auswahlcontainer auf. Nachdem Sie die Eigenschaft oder das Objekt entfernt haben, <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> können Sie zu einem Auswahlcontainer wechseln, der aktualisiert und aufgelistet wurde.

## <a name="change-selection-lists"></a>Auswahllisten ändern

 In diesem Abschnitt fügen Sie eine Auswahlliste für eine grundlegende Eigenschaftsklasse hinzu und wählen mithilfe der Werkzeugfensteroberfläche aus, welche Auswahlliste angezeigt werden soll.

### <a name="to-change-selection-lists"></a>So ändern Sie Auswahllisten

1. Öffnen Sie *MyToolWindow.cs,* und `Simple`fügen Sie eine öffentliche Klasse mit dem Namen hinzu.

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

2. Fügen `SimpleObject` Sie der `MyToolWindow` Klasse eine Eigenschaft sowie zwei Methoden zum Wechseln `Simple` der **Eigenschaftenfensterauswahl** zwischen dem Fensterbereich und dem Objekt hinzu.

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

3. Ersetzen Sie in *MyToolWindowControl.cs*die Kontrollkästchenhandler durch die folgenden Codezeilen:

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

4. Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Öffnen Sie in der experimentellen Instanz das **Fenster MyToolWindow.**

6. Aktivieren Sie das Kontrollkästchen im **Fenster MyToolWindow.** Im **Eigenschaftenfenster** `Simple` werden die Objekteigenschaften **SomeText** und **ReadOnly**angezeigt. Deaktivieren Sie dieses Kontrollkästchen. Die öffentlichen Eigenschaften des Fensters werden im **Eigenschaftenfenster** angezeigt.

    > [!NOTE]
    > Der Anzeigename von **SomeText** ist **Mein Text**.

## <a name="best-practice"></a>Bewährte Methode

In dieser exemplarischen Vorgehensweise wird implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> sodass die wählbare Objektauflistung und die ausgewählte Objektauflistung die gleiche Auflistung sind. Nur das ausgewählte Objekt wird in der Liste Eigenschaftenbrowser angezeigt. Eine vollständigere ISelectionContainer-Implementierung finden Sie in den Beispielen Reference.ToolWindow.

Visual Studio-Toolfenster bleiben zwischen Visual Studio-Sitzungen bestehen. Weitere Informationen zum Beibehalten des Werkzeugfensterstatus finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften und dem Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md)
