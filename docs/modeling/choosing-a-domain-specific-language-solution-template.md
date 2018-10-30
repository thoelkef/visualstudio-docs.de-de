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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d2977d546d463a8c21446a3643cff7ef49a01fb1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908826"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
Um eine DSL-Projektmappe zu erstellen, wählen Sie eine der Lösungsvorlagen, die in den Designer-Assistenten in einer domänenspezifischen Sprache verfügbar sind. Durch Auswählen der Vorlage, die am ehesten entspricht von der Sprache, die Sie erstellen möchten, können Sie den Änderungsaufwand verringern, die Sie an der Lösung ab.

 Die folgenden Vorlagen stehen in den Designer-Assistenten in einer domänenspezifischen Sprache zur Verfügung.

|Vorlage|Features|Beschreibung|
|-|-|-|
|Klassendiagramme|-Depot Formen<br />-Vererbung von Klasse<br />-Der beziehungsvererbung<br />-Form-Vererbung<br />-Die Beziehung Eigenschaften|Verwenden Sie diese Vorlage aus, wenn die domänenspezifischen Sprache enthält, Entitäten und Beziehungen, die über Eigenschaften verfügen. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Klassendiagrammen ähnelt. Die wichtigsten Entitäten sind die Klassen und Schnittstellen zusammen mit der Zuordnung, Generalisierung und die Implementierung von Beziehungen. Eine Klasse oder Schnittstelle wird angezeigt, als ein Feld, das eine Liste der Attribute enthält.|
|Komponentendiagramme|-Ports|Verwenden Sie diese Vorlage, wenn Ihre DSL-Komponenten, d. h., Teile eines Softwaresystems umfasst. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Komponentendiagramme ähnelt. Die wichtigsten Entitäten sind die Komponenten und Ports, die als kleine Formen außerhalb der Komponenten angezeigt werden.|
|Flussdiagramme für Aufgabe|-Image und geometrischer Formen<br />-   *Verantwortlichkeitsbereiche*|Verwenden Sie diese Vorlage aus, wenn Ihre DSL-Workflows, Status oder Sequenzen enthält. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Aktivitätsdiagramme ähnelt. Die main-Entität ist eine Aktivität, und die wichtigste Beziehung ist, einen Übergang zwischen Aktivitäten. Die Vorlage enthält mehrere Elemente wie z. B. Startstatus Endzustand und eine Synchronisierung Leiste.|
|Minimale Sprache|– Ein-Klasse und-Form<br />– Eine Beziehung und Verbinder|Verwenden Sie diese Vorlage, wenn es sich bei Ihrer domänenspezifischen Sprache nicht die anderen Vorlagen ähnelt. Diese Vorlage erstellt eine domänenspezifische Sprache, bei dem zwei-Klassen und eine Beziehung, die dargestellt werden. in der **Toolbox** als **Feld** und **Zeile**. Die Klasse und die Beziehung haben eine Beispiel-Zeichenfolgeneigenschaft.|
|Minimaler WinForm-Designer|– Ein kleines Modell.<br />– Ein Windows-Formular, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, sollten Sie eine Anwendung zu erstellen, in der eine DSL auf einem Windows Form, und nicht auf einem grafischen Designer gebunden ist.<br /><br /> Das Formular, das als Benutzeroberfläche für die Sprache ist im Ordner "Dsl\UI".<br /><br /> Sie sollten das Projekt erstellen, vor dem Formular-Designer zu öffnen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer Windows Forms-Based einer domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimaler WPF-Designer|– Ein kleines Modell<br />– Ein Windows Presentation Foundation-Benutzeroberfläche, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, sollten Sie eine Anwendung zu erstellen, in der eine DSL an eine WPF-Benutzeroberfläche, anstatt in einem grafischen Designer gebunden ist.<br /><br /> Der Designer für die Benutzeroberfläche ist im Ordner "Dsl\UI".<br /><br /> Sie sollten das Projekt erstellen, vor dem Öffnen der Benutzeroberflächen-Designer.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer WPF-Based einer domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL-Bibliothek|– Ein minimal-Bibliothek|Verwenden Sie diese Vorlage, sollten Sie eine partielle DSL-Definition zu erstellen, die in einer anderen DSL-Definitionen importiert werden kann.|

## <a name="see-also"></a>Siehe auch

- [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)
