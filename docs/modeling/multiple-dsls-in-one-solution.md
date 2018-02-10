---
title: "In einer Lösung mehrere konzentriert | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7b1ef7fc26cb0e46ecaf1853d6c9490016e68a5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
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
  
        -   `Dsl*`Projekt als eine **MEF-Komponente**  
  
        -   `DslPackage*`Projekt als eine **MEF-Komponente**  
  
        -   `DslPackage*`Projekt als eine **VS-Paket**  
  
3.  Erstellen Sie die Projektmappe.  
  
 Die resultierende VSIX installiert beide DSLs. Sie können testen, durch Drücken von F5 oder Bereitstellen * YourVsixProject ***\bin\Debug\\\*VSIX**.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Vorgehensweise: Hinzufügen eines Drag-and-Drop-Ereignishandlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)