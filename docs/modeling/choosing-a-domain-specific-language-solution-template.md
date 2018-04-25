---
title: Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6ec2d2210912011e09e439f25ecaa0e21ab6e918
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
Um eine domänenspezifische Sprache-Lösung zu erstellen, wählen Sie eine der Projektmappenvorlagen für, die im Assistenten für domänenspezifische Sprache-Designer verfügbar sind. Durch Auswahl der Vorlage, die am ehesten entspricht von der Sprache, die Sie erstellen möchten, können Sie den Änderungsaufwand verringern, die Sie an der ersten Lösung vorzunehmen.

 Die folgenden Projektmappenvorlagen sind im einer domänenspezifischen Sprache-Designer-Assistenten verfügbar.

|Vorlage|Funktionen|Beschreibung|
|--------------|--------------|-----------------|
|Klassendiagramme|-Depot shapes<br />-Class-Vererbung<br />-Beziehungsvererbung<br />-Form "" Vererbung<br />-Die Beziehungseigenschaften|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache enthält, Entitäten und Beziehungen, die über Eigenschaften verfügen. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Klassendiagramme ähnelt. Die wichtigsten Entitäten sind Klassen und Schnittstellen, zusammen mit der Zuordnung, Generalisierung und Implementierung Beziehungen. Eine Klasse oder Schnittstelle wird als ein Feld, das eine Liste der Attribute enthält.|
|Komponentendiagramme|-Ports|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache Komponenten, d. h., Teile eines Softwaresystems enthält. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Komponentendiagramme ähnelt. Die wichtigsten Entitäten sind Komponenten und Ports, die als kleine Formen außerhalb der Komponenten angezeigt werden.|
|Task-Flow-Diagramme|-Image und Geometry-Formen<br />-   *Verantwortlichkeitsbereiche*|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache Workflows, Status oder Sequenzen enthält. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Aktivitätsdiagramme ähnelt. Hauptentität ist eine Aktivität, und die wichtigsten Beziehung einen Übergang zwischen Aktivitäten. Die Vorlage enthält mehrere Elemente wie z. B. Startzustand Endzustand und eine Synchronisierung Leiste.|
|Minimale Sprache|– Eine Klasse und Form<br />– Eine Beziehung und -connector|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache keinen der anderen Vorlagen ähnelt. Diese Vorlage erstellt eine domänenspezifische Sprache, dessen zwei Klassen und eine Beziehung, die dargestellt werden. in, der **Toolbox** als **Feld** und **Zeile**. Die Klasse und die Beziehung aufweisen eine Beispiel-Zeichenfolge-Eigenschaft.|
|Minimale WinForm-Designer|– Ein kleines Modell.<br />– Ein Windows Form, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, wenn Sie möchten eine Anwendung zu erstellen, in der eine DSL an einem Windows Form, anstatt in einem grafischen Designer gebunden ist.<br /><br /> Das Formular, das als Benutzeroberfläche für die Sprache ist im Ordner "Dsl\UI".<br /><br /> Sie sollten das Projekt vor dem Öffnen der Formular-Designer erstellen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer Windows Forms-Based einer domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimale WPF-Designer|– Ein kleines Modell<br />– Ein Windows Presentation Foundation-Benutzeroberfläche, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, wenn Sie möchten eine Anwendung zu erstellen, in der eine DSL an einem grafischen Designer, anstatt eine WPF-Benutzeroberfläche gebunden ist.<br /><br /> Der Designer für die Benutzeroberfläche ist im Ordner "Dsl\UI".<br /><br /> Das Projekt sollte vor dem Öffnen des UI-Designers erstellt werden.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer WPF-Based einer domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL-Bibliothek|-Eine minimale-Bibliothek|Verwenden Sie diese Vorlage, wenn Sie möchten eine partielle DSL-Definition zu erstellen, die in anderen DSL-Definitionen importiert werden kann.|

## <a name="see-also"></a>Siehe auch

- [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)
