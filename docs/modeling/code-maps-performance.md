---
title: Code Maps sind langsam
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="improve-performance-for-code-maps"></a>Verbessern der Leistung für Code maps

Wenn Sie eine Code Map zum ersten Mal generieren, werden von Visual Studio alle gefundenen Abhängigkeiten indiziert. Dieser Prozess kann einige Zeit, insbesondere bei großen Projektmappen dauern aber höhere Leistung verbessert. Wenn Ihr Code geändert wird, wird von Visual Studio nur der aktualisierte Code neu indiziert. Um die benötigte Zeit für die Karte, um das Rendern zu minimieren, sollten Sie die folgenden Vorschläge aus:

- [Ordnen Sie nur die Abhängigkeiten, die Sie interessieren.](#create-a-code-map-to-see-specific-dependencies)

- Bevor Sie die Code Map für eine gesamte Projektmappe generieren, reduzieren Sie den Umfang der Projektmappe.

- Deaktivieren der automatischen Erstellung der Projektmappe durch Auswahl **Skip Build** auf der Symbolleiste der Code Map.

- Deaktivieren Sie automatische Hinzufügen von übergeordneten Elementen dazu **übergeordnete Elemente einschließen** auf der Symbolleiste der Code Map.

   ![Schaltflächen "Build überspringen" und "Übergeordnete Elemente einschließen"](../modeling/media/codemapsfilterskipbuildicons.png)

- Bearbeiten Sie die Code Map direkt, um Knoten und Links zu entfernen, die Sie nicht benötigen. Das Ändern der Code Map wirkt sich nicht auf den zugrunde liegenden Code aus. Siehe [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Möglicherweise dauert es weitere Maps zu erstellen oder Hinzufügen von Elementen zu einer Zuordnung von **Projektmappen-Explorer** bei der ein Projektelement **in Ausgabeverzeichnis kopieren** -Eigenschaftensatz auf **immer kopieren**. Ändern Sie diese Eigenschaft in **Kopieren, wenn neuer** oder `PreserveNewest`, um die Leistung zu erhöhen. Finden Sie unter [inkrementelle Builds](../msbuild/incremental-builds.md).

Die abgeschlossene Map zeigt die Abhängigkeiten nur für Code an erfolgreich erstellt. Wenn für bestimmte Komponenten Buildfehler auftreten, werden diese Fehler auf der Code Map angezeigt. Vergewissern Sie sich, dass eine Komponente tatsächlich erstellt wird und über Abhängigkeiten verfügt, bevor Sie auf Grundlage der Code Map architekturbezogene Entscheidungen treffen.