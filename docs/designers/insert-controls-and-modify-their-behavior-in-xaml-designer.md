---
title: Einfügen von Steuerelementen und Ändern des Verhaltens im XAML-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: edb657779e8c404032d71061132816a2a30c83c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893453"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Einfügen von Steuerelementen und Ändern des Verhaltens im XAML-Designer

Steuerelemente ermöglichen Benutzern die Interaktion mit Ihrer Anwendung. Verwenden sie zum Sammeln von Informationen und zum Durchführen von Aktionen verwenden, wie z. B. Animieren eines Objekts oder eine Datenquelle.

## <a name="add-controls-to-the-artboard"></a>Hinzufügen von Steuerelementen zur Zeichenfläche

Sie können Steuerelemente über den Bereich **Bestand** auf die **Zeichenfläche**ziehen und sie dann im Fenster **Eigenschaften** ändern.

![Registerkarten-Steuerelement „Objekte“ in Blend](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Erstellen eines Steuerelements aus dem Abbild, einer Form oder einem Pfad

Sie können ein Objekt in ein Steuerelement verwandeln.

![Dialogfeld "Into-Steuerelement erstellen" in Blend](../designers/media/blend_makeintocontrol_xaml.png)

Stellen Sie sich beispielsweise ein Bild von einem Fernseher in der Mitte der Seite vor. Sie können Steuerelemente aus kleinen Bildern konvertieren, die wie TV-Schaltflächen aussehen. Benutzer können dann auf diese Schaltflächen klicken, um den Kanal zu ändern.

Dies ist möglich, da die Schaltflächen nun Steuerelemente sind. Mit den Steuerelementen können Sie auf Benutzerinteraktionen reagieren; in diesem Fall, wenn der Benutzer auf eine Schaltfläche klickt.

Wählen Sie ein Objekt, um ein Steuerelement zu erstellen. Klicken Sie im Menü **Extras** auf **Steuerung erstellen**.

## <a name="make-controls-do-things"></a>Mit Steuerelementen Dinge ausführen

Steuerelemente können Aktionen ausführen, wenn die Benutzer mit ihnen interagieren. Sie können z.B. eine Animation starten, eine Datenquelle aktualisieren oder ein Video abspielen.

Verwenden Sie *Trigger*, *Verhalten*und *Ereignisse* , um mit Steuerelementen etwas auszuführen.

### <a name="triggers"></a>Trigger

Ein *Trigger* ändert eine Eigenschaft oder führt eine Aufgabe als Reaktion auf ein Ereignis oder eine Änderung an einer anderen Eigenschaft aus. Beispielsweise können Sie die Farbe einer Schaltfläche ändern, wenn Benutzer darauf zeigen.

![Der Bereich „Trigger“](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>Verhalten

Ein *Verhalten* ist ein wiederverwendbares Code-Paket. Sie können damit mehr tun als nur Eigenschaften zu ändern. Sie können Aktionen wie das Abfragen eines Datendienstes ausführen. Blend enthält eine kleine Sammlung, Sie können jedoch weitere hinzufügen. Ziehen Sie ein Verhalten auf ein beliebiges Objekt auf der Zeichenfläche und passen Sie das Verhalten durch Festlegen von Eigenschaften an.

![FluidMoveBehavior im Eigenschaftenbereich](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Sehen Sie sich ein Video an:** ![Wiedergabesymbol](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend-Tipps: Einführung in die Verwendung von Verhaltensweisen Teil 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Ereignisse

Für maximale Flexibilität behandeln Sie ein *Ereignis*. Sie müssen Code schreiben.