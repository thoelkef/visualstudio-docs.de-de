---
title: Auswählen einer Vorlage für eine domänenspezifische Sprachlösung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668349"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wählen Sie zum Erstellen einer domänenspezifischen Sprachlösung eine der Lösungs Vorlagen aus, die im Assistenten für domänenspezifische sprach-Designer verfügbar sind. Indem Sie die Vorlage auswählen, die der Sprache am ehesten ähnelt, die Sie erstellen möchten, können Sie die Änderungen minimieren, die Sie an der Start Lösung vornehmen müssen.

 Die folgenden Lösungs Vorlagen sind im Assistenten für domänenspezifische sprach Designer verfügbar.

> [!NOTE]
> Der Zweck der Vorlagen besteht darin, eine Start-DSL bereitzustellen. Die Vorlagen für die Klassen-und Komponenten Diagramme sind keine vollständigen UML-Diagramme. Wenn Sie ein UML-Modell erstellen möchten, sehen Sie sich die UML-Modellierungstools an, die eine Reihe von Diagrammen bereitstellen, die in ein einzelnes Modell integriert werden. Sie sind erweiterbar und können über ModelBus in Ihre DSL integriert werden. Weitere Informationen finden Sie unter [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md).

|Vorlage|Features|BESCHREIBUNG|
|--------------|--------------|-----------------|
|Klassendiagramme|-Depot-Formen<br />-Klassen Vererbung<br />-Beziehungs Vererbung<br />-Shape-Vererbung<br />-Beziehungs Eigenschaften|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Entitäten und Beziehungen enthält, die über Eigenschaften verfügen. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Klassendiagrammen ähnelt. Die Haupt Entitäten sind Klassen und Schnittstellen, zusammen mit Zuordnungs-, Generalisierungs-und Implementierungs Beziehungen. Eine Klasse oder Schnittstelle wird als Feld angezeigt, das eine Liste von Attributen enthält.|
|Komponenten Diagramme|-Ports|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Komponenten enthält, d. h. Teile eines Software Systems. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Komponenten Diagrammen ähnelt. Die Haupt Entitäten sind Komponenten und Ports, die auf der Außenseite der Komponenten als kleine Formen angezeigt werden.|
|Task Flussdiagramme|-Bild-und Geometrie Formen<br />-   *Verantwortlichkeits Bereiche*|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache Workflows, Zustände oder Sequenzen umfasst. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die UML-Aktivitäts Diagrammen ähnelt. Die Haupt Entität ist eine Aktivität, und die Haupt Beziehung ist ein Übergang zwischen Aktivitäten. Die Vorlage enthält mehrere weitere Elemente, wie z. b. Startstatus, Endzustand und eine Synchronisierungs Leiste.|
|Minimal Language (Einfache Version der Sprache)|-Eine Klasse und eine Form<br />-Eine Beziehung und ein Connector|Verwenden Sie diese Lösungs Vorlage, wenn Ihre domänenspezifische Sprache nicht den anderen Vorlagen ähnelt. Mit dieser Vorlage wird eine domänenspezifische Sprache erstellt, die zwei Klassen und eine Beziehung aufweist, die in der **Toolbox** als **Box** und **Line**dargestellt werden. Die-Klasse und die-Beziehung verfügen jeweils über eine Beispiel Zeichenfolgen-Eigenschaft.|
|Minimaler WinForm-Designer|: Ein kleines Modell.<br />-Ein Windows Form, in dem das Modell angezeigt wird.|Verwenden Sie diese Vorlage, wenn Sie eine Anwendung erstellen möchten, in der eine DSL anstelle eines grafischen Designers an ein Windows Form gebunden ist.<br /><br /> Das Formular, das als Benutzeroberfläche für die Sprache fungiert, befindet sich im Ordner "dsl\ui".<br /><br /> Sie sollten das Projekt erstellen, bevor Sie den Formular-Designer öffnen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer Windows Forms basierten domänenspezifischen Sprache](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimaler WPF-Designer|-Ein kleines Modell<br />-Eine Windows Presentation Foundation Benutzeroberfläche, auf der das Modell angezeigt wird.|Verwenden Sie diese Vorlage, wenn Sie eine Anwendung erstellen möchten, in der eine DSL anstelle eines grafischen Designers an eine WPF-Benutzeroberfläche gebunden ist.<br /><br /> Der Designer für die Benutzeroberfläche befindet sich im Ordner "dsl\ui".<br /><br /> Sie sollten das Projekt erstellen, bevor Sie den UI-Designer öffnen.<br /><br /> Weitere Informationen finden Sie unter [Erstellen einer WPF-basierten domänenspezifischen Sprache](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL-Bibliothek|-Eine minimale Bibliothek|Verwenden Sie diese Vorlage, wenn Sie eine partielle DSL-Definition erstellen möchten, die in andere DSL-Definitionen importiert werden kann.|

## <a name="see-also"></a>Weitere Informationen
 [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)
