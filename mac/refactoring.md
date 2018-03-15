---
title: "Umgestalten von Code in Visual Studio für Mac | Microsoft-Dokumentation"
description: "Das Neuorganisieren von Code in Visual Studio für Mac wird durch die Verwendung der Quellanalyse vereinfacht."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: 925c928e171b76af76304074e736fd8962158564
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="refactoring"></a>Umgestaltung

Das Umgestalten von Code ist eine Möglichkeit, vorhandenen Code neu anzuordnen, neu zu strukturieren und zu verdeutlichen, wobei sichergestellt wird, dass das Gesamtverhalten des Codes nicht verändert wird.

Umgestalten erzeugt eine Codebasis mit weniger Fehlern, die für Sie oder andere Entwickler oder Benutzer, die möglicherweise auf den Code verweisen, besser verwendbar, lesbar und verwaltbar ist.

Die Integration in Roslyn, Microsofts Open Source-.NET Compilerplattform, von Visual Studio für Mac ermöglicht mehr Umgestaltungsvorgänge.

## <a name="renaming"></a>Umbenennen 

Der Refactoringbefehl *Umbenennen* kann für jeden Codebezeichner (z.B. Klassenname, Eigenschaftenname usw.) verwendet werden, um alle Vorkommen dieses Bezeichners zu finden und zu ändern. Um ein Symbol umzubenennen, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Umgestalten > Umbenennen** oder die Tastenzuordnung **Cmd + R** aus:

![Menüelement „Umbenennen“](media/refactoring-renaming1.png)

Dadurch werden das Symbol und alle Verweise darauf hervorgehoben. Wenn Sie beginnen, einen neuen Namen einzugeben, werden automatisch alle Verweise in Ihrem Code geändert. Sie können die Fertigstellung der Umbenennung signalisieren, indem Sie die **Eingabetaste** drücken:

 ![Umbenennen und Bezeichner](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Kontextaktionen

Kontextaktionen ermöglichen es Ihnen, jeden C#-Code zu überprüfen und alle Refactoringoptionen anzuzeigen. 

Die Kontextelemente **Auflösen** und **Umgestalten** werden zu einem einzigen Element *Schnelle Problembehebung...* kombiniert, das alle verfügbaren Kontextaktionen für Sie bereitstellt:

![Anzeigen der Kontextelemente](media/refactoring-context-action.png)

Wenn Sie auf beliebige Kontextaktionen zeigen, wird Ihnen eine Vorschau dessen angezeigt, was zu Ihrem Code hinzugefügt oder daraus entfernt wird.

Alternativ können Sie an einer beliebigen Stelle in Ihrem Code **Option + Eingabetaste** drücken:

![Kontextelemente Option + Enter](media/refactoring-image2a.png)

Um diese Optionen zu aktivieren, müssen Sie *Quellanalyse geöffneter Dateien aktivieren* in den Optionen **Visual Studio für Mac > Einstellungen > Texteditor > Quellanalyse** auswählen:

 ![Aktivieren der Quellanalyse](media/refactoring-options.png)

Es existieren mehr als 100 mögliche Aktionen, die vorgeschlagen werden können. Diese können aktiviert bzw. deaktiviert werden können, indem Sie zu **Visual Studio für Mac > Einstellungen > Quellanalyse > C# > Codeaktionen** navigieren und das Kontrollkästchen neben der Aktion aktivieren bzw. deaktivieren:

 ![C#-Quellanalyseaktionen](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Häufig verwendete Kontextaktionen

Einige der am häufigsten verwendeten Kontextaktionen werden nachstehend erläutert.

#### <a name="extract-method"></a>Methode extrahieren

Der Refactoringvorgang „Methode extrahieren“ ermöglicht es Ihnen, eine neue Methode zu erstellen, indem Sie eine Auswahl von Code in einem vorhandenen Member extrahieren. Diese Aktion führt folgende Schritte aus:

* Erstellen einer neuen Methode, die den ausgewählten Code enthält
* Aufrufen der neuen Methode an der Stelle, an der sich der ausgewählte Code befand

##### <a name="example"></a>Beispiel

1. Fügen Sie den folgenden Code hinzu:

```
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Heben Sie die Zeile `double volume = (baseArea * height) / 3;` hervor, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Umgestalten > Methode extrahieren** aus.

3. Verwenden Sie die Pfeiltasten, um auszuwählen, wo die neue Methode in Ihrem Code platziert werden soll.


#### <a name="encapsulate-field"></a>Feld kapseln

Der Vorgang „Feld kapseln“ ermöglicht es Ihnen, eine Eigenschaft von einem vorhandenen Feld aus zu erstellen, und aktualisiert Ihren Code so, dass er auf die neu erstellte Eigenschaft verweist. Indem Sie eine Eigenschaft erstellen, die Ihr Feld kapselt, lassen Sie den Direktzugriff auf Ihr öffentliches Feld nicht zu, d.h. andere Objekte können es nicht ändern.

Diese Aktion führt folgende Schritte aus:

* Ändern des Zugriffsmodifizierers in privat
* Erstellen eines Getters und Setters für das Feld (sofern das Feld nicht schreibgeschützt ist; in diesem Fall wir nur ein Getter erstellt)


## <a name="source-analysis"></a>Quellanalyse

Die Quellanalyse analysiert Ihren Code schnell, indem potenzielle Fehler und Stilverstöße unterstrichen und automatische Korrekturen als Kontextaktionen bereitgestellt werden. 

Sie können alle Ergebnisse der Quellanalyse jeder Datei zu jeder Zeit anzeigen lassen, indem Sie die Scrollleiste an der rechten Seite des Editors anzeigen:

 ![Quellanalyse – Randleiste](media/refactoring-image4a.png)

Wenn Sie auf den Kreis oben klicken, können Sie jeden einzelnen Vorschlag durchlaufen lassen, wobei die schwerwiegendsten Probleme zuerst angezeigt werden. Wenn Sie auf ein einzelnes Ergebnis oder eine einzelne Zeile zeigen, wird das Problem angezeigt, das durch Kontextaktionen behoben werden kann:

 ![Quellanalyseelement](media/refactoring-image5.png)

