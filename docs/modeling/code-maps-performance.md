---
title: Code Maps sind langsam
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28cb2c4fd74716aa876c57517bb440fda513de5d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590539"
---
# <a name="improve-performance-for-code-maps"></a>Verbessern der Leistung von Code Maps

Wenn Sie eine Code Map zum ersten Mal generieren, werden von Visual Studio alle gefundenen Abhängigkeiten indiziert. Dieser Vorgang kann einige Zeit in Anspruch nehmen, insbesondere bei umfangreichen Lösungen, verbessert jedoch die spätere Leistung. Wenn Ihr Code geändert wird, wird von Visual Studio nur der aktualisierte Code neu indiziert. Um die Zeit zu minimieren, die für die Fertigstellung der Zuordnung benötigt wird, sollten Sie die folgenden Vorschläge beachten:

- Stellen Sie nur die Abhängigkeiten in der Code Map dar, die Sie interessieren.

- Bevor Sie die Code Map für eine gesamte Projektmappe generieren, reduzieren Sie den Umfang der Projektmappe.

- Deaktivieren Sie die automatische Erstellung für die Projekt Mappe, indem Sie auf der Symbolleiste Code Map die Option **Build überspringen** auswählen

- Deaktivieren Sie das automatische Hinzufügen von übergeordneten Elementen, indem Sie auf der Symbolleiste Code Map auf übergeordnete Elemente **einschließen**

   ![Schaltflächen "Build überspringen" und "Übergeordnete Elemente einschließen"](../modeling/media/codemapsfilterskipbuildicons.png)

- Bearbeiten Sie die Code Map direkt, um Knoten und Links zu entfernen, die Sie nicht benötigen. Das Ändern der Code Map wirkt sich nicht auf den zugrunde liegenden Code aus. Siehe [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Wenn die Eigenschaft in **Ausgabeverzeichnis kopieren** eines Projekt Elements auf **immer kopieren**festgelegt ist, kann es mehr Zeit in Anspruch nehmen, Maps zu erstellen oder einer **Projektmappen-Explorer** Karte Elemente hinzuzufügen. Ändern Sie diese Eigenschaft in **Kopieren, wenn neuer** oder `PreserveNewest`, um die Leistung zu erhöhen. Siehe [inkrementelle Builds](../msbuild/incremental-builds.md).

Die fertige Zuordnung zeigt Abhängigkeiten nur für Code, der erfolgreich erstellt wurde. Wenn für bestimmte Komponenten Buildfehler auftreten, werden diese Fehler auf der Code Map angezeigt. Vergewissern Sie sich, dass eine Komponente tatsächlich erstellt wird und über Abhängigkeiten verfügt, bevor Sie auf Grundlage der Code Map architekturbezogene Entscheidungen treffen.
