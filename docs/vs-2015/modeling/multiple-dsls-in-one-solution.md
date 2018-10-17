---
title: Mehrere DSLs in einer Projektmappe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ee5bb3213fd7033bb5e3c12f6f9bf8b20c69410f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229471"
---
# <a name="multiple-dsls-in-one-solution"></a>Mehrere DSLs in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mehrere DSLs als Bestandteil einer Projektmappe packen, damit sie zusammen installiert werden.  
  
 Sie können verschiedene Techniken für die Integration mehrerer DSLs nutzen. Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) und [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) und [Anpassen des Verhaltens beim Kopieren](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>So erstellen Sie mehr als eine DSL in einer Projektmappe  
  
1.  Erstellen Sie zwei oder mehr DSL-Projektmappen und ein VSIX-Projekt, und fügen Sie alle Projekte einer Projektmappe hinzu.  
  
    -   Um ein neues VSIX-Projekt zu erstellen: In der **neues Projekt** wählen Sie im Dialogfeld **Visual C#-**, **Erweiterbarkeit**, **VSIX-Projekt**.  
  
    -   Erstellen Sie zwei oder mehr DSL-Projektmappen im Verzeichnis der VSIX-Projektmappe.  
  
         Öffnen Sie für jede DSL eine neue Instanz von Visual Studio. Erstellen Sie die neue DSL, und geben Sie den gleichen Projektmappenordner wie für die VSIX-Projektmappe an.  
  
         Achten Sie darauf, dass Sie jede DSL mit einer anderen Dateinamenerweiterung erstellen.  
  
    -   Ändern Sie die Namen der **Dsl** und **DslPackage** projiziert werden, sodass alle unterschiedlich sind. Beispiel: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   In den einzelnen **DslPackage\*\source.extension.tt**, aktualisieren Sie diese Zeile auf den richtigen Dsl-Projektnamen:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Fügen Sie in der VSIX-Projektmappe Dsl * und DslPackage\* Projekte.  
  
         Sie sollten jedes Paar in einem eigenen Projektmappenordner platzieren.  
  
2.  Kombinieren Sie die VSIX-Manifeste der DSLs:  
  
    1.  Open _ihrvsix-Projekt_**\source.extension.manifest**.  
  
    2.  Wählen Sie für jede DSL **Inhalt hinzufügen** und fügen Sie hinzu:  
  
        -   `Dsl*` Projekt als eine **MEF-Komponente**  
  
        -   `DslPackage*` Projekt als eine **MEF-Komponente**  
  
        -   `DslPackage*` Projekt als eine **Visual Studio-Pakets**  
  
3.  Erstellen Sie die Projektmappe.  
  
 Die resultierende VSIX installiert beide DSLs. Sie können sie mit F5 testen oder bereitstellen _ihrvsix-Projekt_**\bin\Debug\\\*VSIX**.  
  
## <a name="see-also"></a>Siehe auch  
 [Integrieren von Modellen mit Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)



