---
title: "Mehrere DSLs in einer Projektmappe | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Mehrere DSLs in einer Projektmappe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mehrere DSLs als Bestandteil einer Projektmappe packen, damit sie zusammen installiert werden.  
  
 Sie können verschiedene Techniken für die Integration mehrerer DSLs nutzen. Weitere Informationen finden Sie unter [Integrieren von Modellen mit Visual Studio\-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md), [Gewusst wie: Hinzufügen eines Drag & Drop\-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) und [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md).  
  
### So erstellen Sie mehr als eine DSL in einer Projektmappe  
  
1.  Erstellen Sie zwei oder mehr DSL\-Projektmappen und ein VSIX\-Projekt, und fügen Sie alle Projekte einer Projektmappe hinzu.  
  
    -   So erstellen Sie ein VSIX\-Projekt: Wählen Sie im Dialogfeld **Neues Projekt** die Optionen **Visual C\#**, **Erweiterungen** und **VSIX\-Projekt** aus.  
  
    -   Erstellen Sie zwei oder mehr DSL\-Projektmappen im Verzeichnis der VSIX\-Projektmappe.  
  
         Öffnen Sie für jede DSL eine neue Instanz von Visual Studio. Erstellen Sie die neue DSL, und geben Sie den gleichen Projektmappenordner wie für die VSIX\-Projektmappe an.  
  
         Achten Sie darauf, dass Sie jede DSL mit einer anderen Dateinamenerweiterung erstellen.  
  
    -   Ändern Sie die Namen der Projekte **Dsl** und **DslPackage**, sodass alle unterschiedlich sind. Beispiel: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   Ändern Sie in jeder **DslPackage\*\\source.extension.tt** diese Zeile in den richtigen Dsl\-Projektnamen:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Fügen Sie in der VSIX\-Projektmappe die Projekte "Dsl\*" und "DslPackage\*" hinzu.  
  
         Sie sollten jedes Paar in einem eigenen Projektmappenordner platzieren.  
  
2.  Kombinieren Sie die VSIX\-Manifeste der DSLs:  
  
    1.  Öffnen Sie *IhrVSIX\-Projekt***\\source.extension.manifest**.  
  
    2.  Wählen Sie für jede DSL **Inhalt hinzufügen** aus, und fügen Sie Folgendes hinzu:  
  
        -   Das Projekt `Dsl*` als **MEF\-Komponente**  
  
        -   Das Projekt `DslPackage*` als **MEF\-Komponente**  
  
        -   Das Projekt `DslPackage*` als **VS\-Paket**  
  
3.  Erstellen Sie die Projektmappe.  
  
 Die resultierende VSIX installiert beide DSLs. Sie können sie mit F5 testen oder *IhrVSIX\-Projekt***\\bin\\Debug\\\*.vsix** bereitstellen.  
  
## Siehe auch  
 [Integrieren von Modellen mit Visual Studio\-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Gewusst wie: Hinzufügen eines Drag & Drop\-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)