---
title: Einbetten eines Diagramms in ein Windows Form | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669701"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Einbetten eines Diagramms in Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein DSL-Diagramm in ein Windows-Steuerelement einbetten, das im Fenster angezeigt wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="embedding-a-diagram"></a>Einbetten eines Diagramms

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>So Betten Sie ein DSL-Diagramm in ein Windows-Steuerelement ein

1. Fügen Sie dem dslpackage-Projekt eine neue **Benutzer Steuer** Element Datei hinzu.

2. Fügen Sie dem Benutzer Steuerelement ein Panel-Steuerelement hinzu. Dieser Bereich enthält das DSL-Diagramm.

     Fügen Sie weitere Steuerelemente hinzu, die Sie benötigen.

     Legen Sie die Anker Eigenschaften der Steuerelemente fest.

3. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Benutzer Steuerelement Datei, und klicken Sie auf **Code anzeigen**. Fügen Sie den folgenden Konstruktor und die Variable dem Code hinzu:

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDSLDocView docView;

    ```

4. Fügen Sie dem dslpackage-Projekt eine neue Datei mit folgendem Inhalt hinzu:

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

5. Um die DSL zu testen, drücken Sie F5, und öffnen Sie eine Beispielmodell Datei. Das Diagramm wird im-Steuerelement angezeigt. Die Toolbox und andere Features funktionieren normal.

#### <a name="updating-the-form-using-store-events"></a>Aktualisieren des Formulars mithilfe von Store-Ereignissen

1. Fügen Sie im Formular-Designer ein **Listenfeld** mit dem Namen hinzu `listBox1` . Dadurch wird eine Liste der Elemente im Modell angezeigt. Sie wird mit dem Modell mithilfe von *Store-Ereignissen*synchron gehalten. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Überschreiben Sie in der benutzerdefinierten Codedatei weitere Methoden für die DocView-Klasse:

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

3. Fügen Sie im Code hinter dem Benutzer Steuerelement Methoden zum lauschen auf Elemente hinzu, die hinzugefügt und entfernt wurden:

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

4. Um die DSL zu testen, drücken Sie F5, und öffnen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Beispielmodell Datei.

     Beachten Sie, dass im Listenfeld eine Liste der Elemente im Modell angezeigt wird und dass Sie nach dem Hinzufügen oder löschen und nach dem Rückgängigmachen und wiederholen korrekt ist.

## <a name="see-also"></a>Weitere Informationen
 [Navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md) [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
