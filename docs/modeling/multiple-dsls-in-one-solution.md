---
title: Mehrere DSLs in einer Projektmappe
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: aeb20a43c3311fff7aa66d37128003d81a5b18c2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="multiple-dsls-in-one-solution"></a>Mehrere DSLs in einer Projektmappe
Sie können mehrere DSLs als Bestandteil einer Projektmappe packen, damit sie zusammen installiert werden.

 Sie können verschiedene Techniken für die Integration mehrerer DSLs nutzen. Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) und [Vorgehensweise: Fügen Sie einen Drag-and-Drop-Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) und [Kopierverhalten anpassen](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>So erstellen Sie mehr als eine DSL in einer Projektmappe

1.  Erstellen Sie zwei oder mehr DSL-Projektmappen und ein VSIX-Projekt, und fügen Sie alle Projekte einer Projektmappe hinzu.

    -   So erstellen ein neues VSIX-Projekt: In der **neues Projekt** wählen Sie im Dialogfeld **Visual C#-**, **Erweiterbarkeit**, **VSIX-Projekt**.

    -   Erstellen Sie zwei oder mehr DSL-Projektmappen im Verzeichnis der VSIX-Projektmappe.

         Öffnen Sie für jede DSL eine neue Instanz von Visual Studio. Erstellen Sie die neue DSL, und geben Sie den gleichen Projektmappenordner wie für die VSIX-Projektmappe an.

         Achten Sie darauf, dass Sie jede DSL mit einer anderen Dateinamenerweiterung erstellen.

    -   Ändern Sie die Namen der **Dsl** und **DslPackage** projiziert, damit sie alle anderen sind. Beispiel: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

    -   In den einzelnen **DslPackage\*\source.extension.tt**, aktualisieren Sie diese Zeile auf den richtigen Namen der Dsl-Projekt:

         `string dslProjectName = "Dsl2";`

    -   Fügen Sie in die VSIX-Projektmappe Dsl * und DslPackage\* Projekte.

         Sie sollten jedes Paar in einem eigenen Projektmappenordner platzieren.

2.  Kombinieren Sie die VSIX-Manifeste der DSLs:

    1.  Open * YourVsixProject ***\source.extension.manifest**.

    2.  Wählen Sie für jede DSL **Inhalt hinzufügen** und hinzufügen:

        -   `Dsl*` Projekt als eine **MEF-Komponente**

        -   `DslPackage*` Projekt als eine **MEF-Komponente**

        -   `DslPackage*` Projekt als eine **VS-Paket**

3.  Erstellen Sie die Projektmappe.

 Die resultierende VSIX installiert beide DSLs. Sie können testen, durch Drücken von F5 oder Bereitstellen * YourVsixProject ***\bin\Debug\\\*VSIX**.

## <a name="see-also"></a>Siehe auch

- [Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)