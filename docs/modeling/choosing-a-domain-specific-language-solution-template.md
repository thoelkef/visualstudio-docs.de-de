---
title: "Auswählen einer domänenspezifischen Sprache Projektmappenvorlage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: b636ab7937c85199c26b8ce8a95fa33cdcc7976b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
Um eine domänenspezifische Sprache-Lösung zu erstellen, wählen Sie eine der Projektmappenvorlagen für, die im Assistenten für domänenspezifische Sprache-Designer verfügbar sind. Durch Auswahl der Vorlage, die am ehesten entspricht von der Sprache, die Sie erstellen möchten, können Sie den Änderungsaufwand verringern, die Sie an der ersten Lösung vorzunehmen.  
  
 Die folgenden Projektmappenvorlagen sind im einer domänenspezifischen Sprache-Designer-Assistenten verfügbar.  
  
|Vorlage|Features|Beschreibung|  
|--------------|--------------|-----------------|  
|Klassendiagramme|-Depot shapes<br />-Class-Vererbung<br />-Beziehungsvererbung<br />-Form "" Vererbung<br />-Die Beziehungseigenschaften|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache enthält, Entitäten und Beziehungen, die über Eigenschaften verfügen. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Klassendiagramme ähnelt. Die wichtigsten Entitäten sind Klassen und Schnittstellen, zusammen mit der Zuordnung, Generalisierung und Implementierung Beziehungen. Eine Klasse oder Schnittstelle wird als ein Feld, das eine Liste der Attribute enthält.|  
|Komponentendiagramme|-Ports|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache Komponenten, d. h., Teile eines Softwaresystems enthält. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Komponentendiagramme ähnelt. Die wichtigsten Entitäten sind Komponenten und Ports, die als kleine Formen außerhalb der Komponenten angezeigt werden.|  
|Task-Flow-Diagramme|-Image und Geometry-Formen<br />-   *Verantwortlichkeitsbereiche*|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache Workflows, Status oder Sequenzen enthält. Diese Vorlage erstellt eine domänenspezifische Sprache, die UML-Aktivitätsdiagramme ähnelt. Hauptentität ist eine Aktivität, und die wichtigsten Beziehung einen Übergang zwischen Aktivitäten. Die Vorlage enthält mehrere Elemente wie z. B. Startzustand Endzustand und eine Synchronisierung Leiste.|  
|Minimale Sprache|– Eine Klasse und Form<br />– Eine Beziehung und -connector|Verwenden Sie diese Projektmappe (Vorlage), wenn Ihre einer domänenspezifischen Sprache keinen der anderen Vorlagen ähnelt. Diese Vorlage erstellt eine domänenspezifische Sprache, dessen zwei Klassen und eine Beziehung, die dargestellt werden. in, der **Toolbox** als **Feld** und **Zeile**. Die Klasse und die Beziehung aufweisen eine Beispiel-Zeichenfolge-Eigenschaft.|  
|Minimale WinForm-Designer|– Ein kleines Modell.<br />– Ein Windows Form, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, wenn Sie möchten eine Anwendung zu erstellen, in der eine DSL an einem Windows Form, anstatt in einem grafischen Designer gebunden ist.<br /><br /> Das Formular, das als Benutzeroberfläche für die Sprache ist im Ordner "Dsl\UI".<br /><br /> Sie sollten das Projekt vor dem Öffnen der Formular-Designer erstellen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer Windows Forms-Based einer domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Minimale WPF-Designer|– Ein kleines Modell<br />– Ein Windows Presentation Foundation-Benutzeroberfläche, in dem das Modell angezeigt.|Verwenden Sie diese Vorlage, wenn Sie möchten eine Anwendung zu erstellen, in der eine DSL an einem grafischen Designer, anstatt eine WPF-Benutzeroberfläche gebunden ist.<br /><br /> Der Designer für die Benutzeroberfläche ist im Ordner "Dsl\UI".<br /><br /> Das Projekt sollte vor dem Öffnen des UI-Designers erstellt werden.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer WPF-Based einer domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|DSL-Bibliothek|-Eine minimale-Bibliothek|Verwenden Sie diese Vorlage, wenn Sie möchten eine partielle DSL-Definition zu erstellen, die in anderen DSL-Definitionen importiert werden kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)
