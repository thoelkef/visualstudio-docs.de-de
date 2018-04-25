---
title: Einbetten eines Diagramms in Windows Form
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 75e7c058d1cc852386e1df897127b96781b60c50
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Einbetten eines Diagramms in Windows Form
Sie können einen DSL-Diagramm einbetten, in einem Windows-Steuerelement, die in angezeigt wird der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fenster.

## <a name="embedding-a-diagram"></a>Einbetten eines Diagramms

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Eine DSL-Diagramm in ein Windows-Steuerelement eingebettet werden sollen.

1.  Fügen Sie einen neuen **Benutzersteuerelement** Datei zum Projekt DslPackage.

2.  Fügen Sie ein Panel-Steuerelement auf das Benutzersteuerelement hinzu. In diesem Bereich wird der DSL-Diagramm enthalten.

     Fügen Sie andere Steuerelemente, die erforderlich sind.

     Legen Sie die Premium-Eigenschaften der Steuerelemente.

3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste die Benutzersteuerelementdatei, und klicken Sie auf **Code anzeigen**. Fügen Sie diesen Konstruktor und die Variable an den Code hinzu:

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;

    ```

4.  Fügen Sie eine neue Datei zum Projekt DslPackage mit dem folgenden Inhalt hinzu:

    ```
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }

    ```

5.  Drücken Sie F5, und öffnen Sie eine Beispieldatei für das Modell, zum Testen der DSL. Das Diagramm wird innerhalb des Steuerelements angezeigt. Die Toolbox und andere Funktionen funktionieren ordnungsgemäß.

#### <a name="updating-the-form-using-store-events"></a>Aktualisieren das Formular mit Speicher-Ereignisse

1.  Fügen Sie in den Formular-Designer eine **ListBox** mit dem Namen `listBox1`. Dadurch wird eine Liste der Elemente im Modell angezeigt. Es bleiben in Synchronism mit dem Modell unter Verwendung *Speichern von Ereignissen*. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2.  Überschreiben Sie in der Datei mit benutzerdefiniertem Code weitere Methoden, um die DocView-Klasse:

    ```

    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }

    ```

3.  Fügen Sie im Code hinter das Benutzersteuerelement Methoden zum Abhören von Elemente hinzugefügt und entfernt:

    ```

          public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }

    ```

4.  Drücken Sie F5, um die DSL zu testen, und klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie eine Beispieldatei für das Modell.

     Beachten Sie, dass im Listenfeld eine Liste der Elemente im Modell angezeigt wird, und er korrekt ist, nachdem alle hinzufügen oder löschen und rückgängig und wiederholen.

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
