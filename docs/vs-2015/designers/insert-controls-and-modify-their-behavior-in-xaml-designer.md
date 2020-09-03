---
title: Einfügen von Steuerelementen und Ändern des Verhaltens im XAML-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02d51c5799391863262d285e1cda209a3b7938d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300848"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Einfügen von Steuerelementen und Ändern des Verhaltens im XAML-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Steuerelemente ermöglichen Benutzern die Interaktion mit Ihrer Anwendung. Verwenden sie zum Sammeln von Informationen und zum Durchführen von Aktionen verwenden, wie z. B. Animieren eines Objekts oder eine Datenquelle.

 **In diesem Thema:**

- [Hinzufügen von Steuerelementen zur Zeichenfläche](#Insert)

- [Mit Steuerelementen Dinge ausführen](#Modify)

## <a name="add-controls-to-the-artboard"></a><a name="Insert"></a> Hinzufügen von Steuerelementen zur Zeichenfläche
 Sie können Steuerelemente über den Bereich **Bestand** auf die **Zeichenfläche**ziehen und sie dann im Fenster **Eigenschaften** ändern.

 ![Blend-&#45; Assets &#45; flipview](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")

 In diesen Videos erfahren Sie, wie Sie einige der häufigeren Steuerelemente verwenden.

|Control|Sehen Sie sich ein kurzes Video an|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen der Steuerelemente](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Entwerfen einer Schaltfläche](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen von Bildern zu einem TextBlock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Erstellen Sie einen Schieberegler mit einer](https://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A) QuickInfo.|
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [funktioniert mit einem GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Erstellen eines Steuerelements aus dem Abbild, einer Form oder einem Pfad
 Sie können ein Objekt in ein Steuerelement verwandeln.

 ![Dialogfeld "Into-Steuerelement erstellen" in Blend](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")

 Stellen Sie sich beispielsweise ein Bild von einem Fernseher in der Mitte der Seite vor. Sie können Steuerelemente aus kleinen Bildern konvertieren, die wie TV-Schaltflächen aussehen. Benutzer können dann auf diese Schaltflächen klicken, um den Kanal zu ändern.

 Dies ist möglich, da die Schaltflächen nun Steuerelemente sind. Mit den Steuerelementen können Sie auf Benutzerinteraktionen reagieren; in diesem Fall, wenn der Benutzer auf eine Schaltfläche klickt.

 Wählen Sie ein Objekt, um ein Steuerelement zu erstellen. Klicken Sie im Menü **Extras** auf **Steuerung erstellen**.

## <a name="make-controls-do-things"></a><a name="Modify"></a> Ausführen von Steuerelementen
 Steuerelemente können Aktionen ausführen, wenn die Benutzer mit ihnen interagieren. Sie können z. B. eine Animation starten, eine Datenquelle aktualisieren oder ein Video abspielen.

 Verwenden Sie *Trigger*, *Verhalten*und *Ereignisse* , um mit Steuerelementen etwas auszuführen.

### <a name="triggers"></a>Auslöser
 Ein *Trigger* ändert eine Eigenschaft oder führt eine Aufgabe als Reaktion auf ein Ereignis oder eine Änderung an einer anderen Eigenschaft aus. Beispielsweise können Sie die Farbe einer Schaltfläche ändern, wenn Benutzer darauf zeigen.

 ![Der Bereich "Trigger"](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen eines Eigenschaften Auslösers](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger)

### <a name="behaviors"></a>Verhalten
 Ein *Verhalten* ist ein wiederverwendbares Code-Paket. Sie können damit mehr tun als nur Eigenschaften zu ändern. Sie können Aktionen wie das Abfragen eines Datendienstes ausführen. Blend enthält eine kleine Sammlung, Sie können jedoch weitere hinzufügen. Ziehen Sie ein Verhalten auf ein beliebiges Objekt auf der Zeichenfläche und passen Sie das Verhalten durch Festlegen von Eigenschaften an.

 ![FluidMoveBehavior im Eigenschaftenbereich](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend-Tipps: Einführung in die Verwendung von Verhalten Teil 1](https://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Events
 Für maximale Flexibilität behandeln Sie ein *Ereignis*. Sie müssen Code schreiben.

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen eines Maus Ereignisses](https://www.youtube.com/watch?v=2PMxAlb-x_E).
