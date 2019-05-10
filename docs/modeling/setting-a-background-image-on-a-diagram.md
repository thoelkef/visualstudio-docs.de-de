---
title: Festlegen eines Hintergrundbilds für ein Diagramm
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e79a7fd37bd5f2d5298bda6dca7568c6ba4db6ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823956"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Festlegen eines Hintergrundbilds für ein Diagramm
In Visual Studio-Visualisierungs- und Modellierungs-SDK können Sie das Hintergrundbild für einen generierten Designer mithilfe von benutzerdefiniertem Code festlegen.

## <a name="setting-the-background-image"></a>Festlegen des Hintergrundbildes

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>So legen Sie ein Hintergrundbild für einen generierten Designer fest

1. Kopieren Sie die Bilddatei, die Sie als Diagrammhintergrund verwenden möchten, in das Verzeichnis "Dsl\Resources" des aktuellen Projekts.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner "Dsl\Resources", zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Element**.

3. In der **vorhandenes Element hinzufügen** (Dialogfeld), navigieren Sie zu dem Ordner "Dsl\Resources".

4. In der **Dateityp** auf **Bilddateien**.

5. Klicken Sie auf die Bilddatei, die Sie in das Verzeichnis kopiert, und klicken Sie dann auf **hinzufügen**.

6. Mit der rechten Maustaste Dsl, und klicken Sie auf **Eigenschaften** um die Eigenschaften des Dsl-Projekt zu öffnen.

7. Auf der **Ressourcen** auf **dieses Projekt enthält keine Standardressourcendatei. Klicken Sie hier, um eine zu erstellen.**

8. Die Bilddatei der Ressourcendatei hinzuzufügen, ziehen Sie das Bild aus **Projektmappen-Explorer** in das Fenster "Ressourcen".

9. Öffnen Sie das Menü "Datei", und klicken Sie auf die Option zum Speichern der Projekteigenschaften.

10. Prüfen Sie, ob die Datei "Dsl\Properties\Resources.resx" vorhanden ist und die Datei "Resources.Designer.cs" enthält.

11. Wenn "Resources.Designer.cs" fehlt, klicken Sie auf die Datei "Resources.resx" im **Projektmappen-Explorer**.

12. Legen Sie im Fenster **Eigenschaften** die Eigenschaft `Custom Tool` auf `ResXFileCodeGenerator`fest.

13. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Dsl-Projekts, zeigen Sie auf **hinzufügen**, und klicken Sie auf **neuer Ordner**.

14. Nennen Sie den Ordner **benutzerdefinierte**.

15. Mit der rechten Maustaste in den Ordner "Custom", zeigen Sie auf **hinzufügen**, und klicken Sie auf **neues Element**.

16. In der **neues Element hinzufügen** Dialogfeld die **Vorlagen** auf **Codedatei**.

17. In der **Namen** geben `BackgroundImage.cs`, und klicken Sie auf **hinzufügen**.

18. Kopieren Sie den folgenden Code in die Datei "BackgroundImage.cs", und passen Sie den Namespace, den Diagrammklassennamen und den Bilddatei-Ressourcennamen an.

     Ersetzen Sie "MyDiagramClass" durch den Namen der partiellen Diagrammklasse, die in "Dsl\GeneratedCode\Diagrams.cs" definiert ist. Den richtigen Namespace können Sie auch aus der Datei "Dsl\GeneratedCode\Diagrams.cs" abrufen.

    ```csharp
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

## <a name="see-also"></a>Siehe auch

- [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)
- [Anpassen von Text- und Image-Feldern](../modeling/customizing-text-and-image-fields.md)
- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
