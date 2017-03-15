---
title: "Festlegen eines Hintergrundbilds f&#252;r ein Diagramm | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# Festlegen eines Hintergrundbilds f&#252;r ein Diagramm
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Visualisierungs\- und Modellierungs\-SDK von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie das Hintergrundbild für einen generierten Designer mithilfe von benutzerdefiniertem Code festlegen.  
  
## Festlegen des Hintergrundbildes  
  
#### So legen Sie ein Hintergrundbild für einen generierten Designer fest  
  
1.  Kopieren Sie die Bilddatei, die Sie als Diagrammhintergrund verwenden möchten, in das Verzeichnis "Dsl\\Resources" des aktuellen Projekts.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Ordner "Dsl\\Resources", zeigen Sie auf **Hinzufügen**, und klicken Sie anschließend auf **Vorhandenes Element**.  
  
3.  Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zum Ordner "Dsl\\Resources".  
  
4.  Klicken Sie in der Dropdownliste **Dateityp** auf **Bilddateien**.  
  
5.  Klicken Sie auf die Bilddatei, die Sie in das Verzeichnis kopiert haben, und klicken Sie dann auf **Hinzufügen**.  
  
6.  Klicken Sie mit der rechten Maustaste auf "Dsl", und klicken Sie auf **Eigenschaften**, um die Eigenschaften des Projekts "Dsl" zu öffnen.  
  
7.  Klicken Sie auf der Registerkarte **Ressourcen** auf **Dieses Projekt enthält keine Standardressourcendatei. Klicken Sie hier, um eine zu erstellen.**  
  
8.  Fügen Sie die Bilddatei der Ressourcendatei hinzu, indem Sie das Bild aus dem **Projektmappen\-Explorer** in das Ressourcenfenster ziehen.  
  
9. Öffnen Sie das Menü "Datei", und klicken Sie auf die Option zum Speichern der Projekteigenschaften.  
  
10. Prüfen Sie, ob die Datei "Dsl\\Properties\\Resources.resx" vorhanden ist und die Datei "Resources.Designer.cs" enthält.  
  
11. Wenn "Resources.Designer.cs" fehlt, klicken Sie im **Projektmappen\-Explorer** auf die Datei "Resources.resx".  
  
12. Legen Sie im Fenster **Eigenschaften** für die `Custom Tool`\-Eigenschaft den Wert `ResXFileCodeGenerator` fest.  
  
13. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt "Dsl", zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neuer Ordner**.  
  
14. Geben Sie dem Ordner den Namen "Custom".  
  
15. Klicken Sie mit der rechten Maustaste auf den Ordner "Custom", zeigen Sie auf **Hinzufügen**, und klicken Sie auf **Neues Element**.  
  
16. Klicken Sie im Dialogfeld **Neues Element hinzufügen** im Feld **Vorlagen** auf **Codedatei**.  
  
17. Geben Sie Feld **Name** den Dateinamen `BackgroundImage.cs` ein, und klicken Sie auf **Hinzufügen**.  
  
18. Kopieren Sie den folgenden Code in die Datei "BackgroundImage.cs", und passen Sie den Namespace, den Diagrammklassennamen und den Bilddatei\-Ressourcennamen an.  
  
     Ersetzen Sie "MyDiagramClass" durch den Namen der partiellen Diagrammklasse, die in "Dsl\\GeneratedCode\\Diagrams.cs" definiert ist.  Den richtigen Namespace können Sie auch aus der Datei "Dsl\\GeneratedCode\\Diagrams.cs" abrufen.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Siehe auch  
 [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)   
 [Anpassen von Text\- und Image\-Feldern](../modeling/customizing-text-and-image-fields.md)   
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)