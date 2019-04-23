---
title: Einbetten eines Diagramms in einem Windows Form | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 440b60697d4ab1e88f535b6c5ef824bc74e19c48
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068690"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Einbetten eines Diagramms in Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einem DSL-Diagramm in einem Windows-Steuerelement angezeigt wird, Einbetten der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fenster.  
  
## <a name="embedding-a-diagram"></a>Einbetten eines Diagramms  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Zum Einbetten von einem DSL-Diagramm in einem Windows-Steuerelement  
  
1. Fügen Sie einen neuen **Benutzersteuerelement** Datei DslPackage-Projekt.  
  
2. Fügen Sie ein Panel-Steuerelement, auf das Benutzersteuerelement. In diesem Bereich wird das DSL-Diagramm enthalten.  
  
     Fügen Sie andere Steuerelemente, die erforderlich sind.  
  
     Legen Sie die Anker-Eigenschaften der Steuerelemente.  
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste der Benutzersteuerelement-Datei, und klicken Sie auf **Ansichtscode**. Fügen Sie diesen Konstruktor und die Variable auf den Code hinzu:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4. Fügen Sie eine neue Datei in das DslPackage-Projekt mit dem folgenden Inhalt hinzu:  
  
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
  
5. Um die DSL zu testen, drücken Sie F5, und öffnen Sie eine beispielmodelldatei. Das Diagramm auf das Steuerelement angezeigt wird. Die Toolbox und andere Funktionen funktionieren ordnungsgemäß.  
  
#### <a name="updating-the-form-using-store-events"></a>Aktualisieren das Formular mit der Store-Ereignisse  
  
1. Fügen Sie in den Formular-Designer eine **ListBox** mit dem Namen `listBox1`. Dadurch wird eine Liste der Elemente im Modell angezeigt. Sie bleiben im Synchronism mit dem Modell mit *Speichern von Ereignissen*. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2. Überschreiben Sie in der Datei mit benutzerdefiniertem Code weitere Methoden, um die DocView--Klasse:  
  
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
  
3. Fügen Sie in den Code-behind das Benutzersteuerelement Methoden zum Lauschen auf die Elemente hinzugefügt und entfernt:  
  
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
  
4. Drücken Sie F5, um die DSL zu testen, und klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], öffnen Sie eine beispielmodelldatei.  
  
     Beachten Sie, dass im Listenfeld eine Liste der Elemente im Modell angezeigt wird und er korrekt ist, nachdem alle Hinzufügungen oder löschungen und rückgängig und wiederholen.  
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
