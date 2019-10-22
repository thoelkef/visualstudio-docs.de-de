---
title: Workflow-Designer Shellfeatures | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606601"
---
# <a name="workflow-designer-shell-features"></a>Workflow-Designer-Shellfunktionen
Die [!INCLUDE[wfd1](../includes/wfd1-md.md)]-Benutzeroberfläche besteht aus drei Hauptbereichen: der Designeroberfläche, der Breadcrumb-Leiste darüber und der Shell darunter. Die Breadcrumb-Leiste am oberen Fensterrand dient zur Anzeige der Vorgängerliste für die aktuelle Stammaktivität. [!INCLUDE[crdefault](../includes/crdefault-md.md)] Gewusst[wie: Verwenden der Breadcrumb-Navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). Die Designeroberfläche im mittleren Bereich dient zum Erstellen von Workflows. Die Shell am unteren Fensterrand enthält eine Reihe von Schaltflächen zum Verwalten der aktuellen Ansicht.

## <a name="shell-features"></a>Shell-Funktionen
 Auf der rechten Seite der Shell-Leiste befinden sich Schaltflächen zum Vergrößern bzw. Verkleinern der Workflowgrafik, zum Anpassen des Workflowinhalts an die Bildschirmgröße und zum Einblenden bzw. Ausblenden der Übersichtskarte. Sie können die Workflowgrafik auch mit den Tastenkombinationen STRG++ und STRG+- vergrößern bzw. verkleinern.

## <a name="overview-map"></a>Übersichtskarte
 Die Übersichtskarte zeigt eine kleine Version der gesamten Aktivität des aktuellen Breadcrumb-Stamms an, einschließlich aller untergeordneten Elemente mit erweiterten untergeordneten Elementen. Der aktuell im Editor angezeigte Teil der Aktivität wird in einem Ansichtsfenster, einem Rechteck mit orangefarbenem Rahmen, hervorgehoben. Durch Ziehen des Rechtecks auf der Übersichtskarte können Sie im Workflow-Designer einen Bildlauf durchführen und die Ansicht des Editors ändern.

> [!NOTE]
> Die [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Benutzeroberfläche ist virtualisiert. Die Aktivitätsdesigner werden nur nach Bedarf gerendert. Die Teile des Workflows, die auf der Designeroberfläche nicht gezeichnet wurden, werden in der Übersichtskarte weiß angezeigt. Um den Workflow vollständig zu zeichnen, führen Sie einen Bildlauf auf der Übersichtskarte durch.

## <a name="copying-or-saving-workflows-as-images"></a>Kopieren und Speichern von Workflows als Bilder
 Workflows können im Bitmapformat kopiert und im Bitmap- oder Vektorformat gespeichert werden. Das Kopieren bzw. Speichern eines Bilds bietet die Möglichkeit, eine Ansicht der gesamten Aktivität des aktuellen Breadcrumb-Stamms in ein anderes Programm zu exportieren, einschließlich aller untergeordneten Elemente und zugehörigen erweiterten untergeordneten Elemente.

 Zum Kopieren als Bild klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Designer, und wählen Sie **als Bild kopieren**aus. Zum Speichern als Bild klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Designer, und wählen Sie **als Bild speichern**aus. Workflows können in den Formaten JPG, PNG, GIF und XPS gespeichert werden. Das Format wird im Dialogfeld **Speichern** unter im Dropdown-Listenfeld **Dateityp:** am unteren Rand des Fensters ausgewählt.

## <a name="fonts-and-colors"></a>Schriftarten und Farben
 Die im [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] verwendeten Schriftarten hängen von der Umgebungsschriftart ab. Die Farben im [!INCLUDE[wfd2](../includes/wfd2-md.md)] ändern sich, wenn Sie in den Betriebssystemeinstellungen ein Farbschema mit hohem Kontrast wählen. Sie müssen [!INCLUDE[vs2010](../includes/vs2010-md.md)] neu starten, nachdem Sie eine Änderung an den Schriftart- oder Farbeinstellungen vorgenommen haben, damit die Änderungen in den [!INCLUDE[wfd2](../includes/wfd2-md.md)] übernommen werden.