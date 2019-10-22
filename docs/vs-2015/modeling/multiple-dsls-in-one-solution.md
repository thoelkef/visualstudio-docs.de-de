---
title: Mehrere DSLs in einer Projekt Mappe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668552"
---
# <a name="multiple-dsls-in-one-solution"></a>Mehrere DSLs in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mehrere DSLs als Bestandteil einer Projektmappe packen, damit sie zusammen installiert werden.

 Sie können verschiedene Techniken für die Integration mehrerer DSLs nutzen. Weitere Informationen finden Sie unter [integrieren von Modellen mithilfe von Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) und Gewusst [wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) und [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>So erstellen Sie mehr als eine DSL in einer Projektmappe

1. Erstellen Sie zwei oder mehr DSL-Projektmappen und ein VSIX-Projekt, und fügen Sie alle Projekte einer Projektmappe hinzu.

   - So erstellen Sie ein neues VSIX-Projekt: Wählen Sie im Dialogfeld " **Neues Projekt** " die Option **Visualisierung C#** , **Erweiterbarkeit**und **VSIX-Projekt**aus.

   - Erstellen Sie zwei oder mehr DSL-Projektmappen im Verzeichnis der VSIX-Projektmappe.

        Öffnen Sie für jede DSL eine neue Instanz von Visual Studio. Erstellen Sie die neue DSL, und geben Sie den gleichen Projektmappenordner wie für die VSIX-Projektmappe an.

        Achten Sie darauf, dass Sie jede DSL mit einer anderen Dateinamenerweiterung erstellen.

   - Ändern Sie die Namen der **DSL** -und **dslpackage** -Projekte, sodass Sie sich alle unterscheiden. Beispiel: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Aktualisieren Sie diese Zeile in jedem **dslpackage-\* \ Source.Extension.tt**auf den richtigen DSL-Projektnamen:

        `string dslProjectName = "Dsl2";`

   - Fügen Sie in der VSIX-Projekt Mappe die Projekte "DSL *" und "dslpackage \*" hinzu.

        Sie sollten jedes Paar in einem eigenen Projektmappenordner platzieren.

2. Kombinieren Sie die VSIX-Manifeste der DSLs:

   1. Öffnen Sie _yourvsixproject_ **\source.Extension.Manifest**.

   2. Wählen Sie für jede DSL **Inhalt hinzufügen** und hinzufügen aus:

       - `Dsl*` Projekt als **MEF-Komponente**

       - `DslPackage*` Projekt als **MEF-Komponente**

       - `DslPackage*` Projekt als **vs-Paket**

3. Erstellen Sie die Projektmappe.

   Die resultierende VSIX installiert beide DSLs. Sie können Sie mit F5 testen oder _yourvsixproject_ **\bin\debug \\ \*. vsix**bereitstellen.

## <a name="see-also"></a>Siehe auch
 [Integrieren von Modellen mithilfe von Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) Gewusst [wie: Hinzufügen eines Drag & amp; Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md)
