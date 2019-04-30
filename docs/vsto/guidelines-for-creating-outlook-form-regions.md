---
title: Richtlinien zum Erstellen von Outlook-Formularbereichen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d48a3ad24d094d0ebc822b572f2521eaefae5356
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826495"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Richtlinien zum Erstellen von Outlook-Formularbereichen
  Anhand der folgenden Informationen können Formularbereiche optimiert und mögliche Probleme vermieden werden:

- [Verwenden von Formularbereichsnamen](#UsingFormRegions).

- [Deaktivieren von formularbereichsvererbung](#DisablingInheritance).

- [Arten kennen und Klasse-Nachrichtennamen](#ClassNames).

- [Entwurf, die benachbarten Formularbereichen für den Lesebereich](#ReadingPane).

- [Verwenden von optimalen Symbolgrößen](#UsingOptimal).

  Weitere Informationen zu Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="UsingFormRegions"></a> Verwenden von Formularbereichsnamen
 Der Formularbereich wird mit mehreren Namen beschrieben. Es ist wichtig, den Unterschied zwischen diesen Namen und den jeweiligen Einfluss auf den Formularbereich zu kennen. In der folgenden Tabelle wird jeder Name beschrieben.

|Formularbereichsname|Beschreibung|
|----------------------|-----------------|
|Formularbereichs-Elementname|Der Name, den Sie für das **Outlook-Formularbereich** -Element im Dialogfeld **Neues Element hinzufügen** angeben. Dies ist der Name der Formularbereich-Codedatei, die im **Projektmappen-Explorer**angezeigt wird.|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> -Eigenschaft|Dieser Name wird auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** des Assistenten **Neuer Outlook-Formularbereich** angegeben. Dieser Name wird als **FormRegionName** -Eigenschaft im Fenster **Eigenschaften** angezeigt.<br /><br /> Verwenden Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> -Eigenschaft, um die Bezeichnung anzugeben, durch die der Formularbereich in der Outlook-Benutzeroberfläche identifiziert wird. In separaten Formularbereichen wird dieser Name als Schaltfläche auf dem Menüband des Outlook-Elements angezeigt.<br /><br /> In benachbarten Formularbereichen wird dieser Name als Headertext über dem Formularbereich angezeigt.|
|`Microsoft.Office.Tools.Outlook.FormRegionName` Attribut|Wird dem Projekt ein **Outlook-Formularbereich** -Element hinzugefügt, legt Visual Studio diese Eigenschaft auf den vollqualifizierten Namen des Formularbereichs fest. Der standardmäßige vollqualifizierte Name ist der Name des VSTO-Add-Ins, das durch einen Punkt mit dem Namen des Formularbereichs verbunden ist (beispielsweise `OutlookAddIn1.FormRegion1`).<br /><br /> Dieser vollqualifizierte Name wird am Anfang der Factoryklasse für den Formularbereich auch als Attribut angezeigt.<br /><br /> Verwenden Sie das `Microsoft.Office.Tools.Outlook.FormRegionName`-Attribut, um den Formularbereich in allen Outlook-VSTO-Add-Ins eindeutig zu identifizieren. Der Wert des `Microsoft.Office.Tools.Outlook.FormRegionName`-Attributs kann nicht durch Umbenennen des Formularbereichs oder durch Ändern der <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>-Eigenschaft geändert werden. Um diesen Namen zu ändern, muss das `Microsoft.Office.Tools.Outlook.FormRegionName`-Attribut in der Formularbereich-Codedatei geändert werden.|

## <a name="DisablingInheritance"></a> Deaktivieren von formularbereichsvererbung
 Standardmäßig erbt eine benutzerdefinierte Nachrichtenklasse alle Formularbereichzuordnungen der Basisnachrichtenklasse. Beispielsweise wird eine Nachrichtenklasse mit dem Namen `IPM.Task.Contoso` von `IPM.Task` abgeleitet. Daher erbt `IPM.Task.Contoso` die Formularbereichzuordnungen von `IPM.Task`.

 Soll der Formularbereich abgeleiteten Nachrichtenklassen zugeordnet werden, legen Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> -Eigenschaft des Formularbereichs auf **true**. Z. B., wenn Sie einen benachbarter Formularbereich zuordnen `IPM.Task` und legen Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> Eigenschaft **"true"**, wird der Formularbereich nur an das Ende eines standardmäßigen Aufgabenformulars angehängt werden. Der Formularbereich wird nicht an den unteren Bereich von angepassten Versionen eines standardmäßigen Aufgabenformulars angehängt.

## <a name="ClassNames"></a> Grundlegendes zu Typen und Nachrichtenklassennamen
 Der Typname eines Outlook-Elements unterscheidet sich vom Namen der Nachrichtenklasse eines Outlook-Elements. Beispielsweise ist der Typname eines RSS-Elements `Microsoft.Office.Interop.Outlook.PostItem`. Der Nachrichtenklassenname eines RSS-Elements ist `IPM.Post.RSS`.

 Verwenden Sie den Typnamen, um auf ein Outlook-Element in Code zu verweisen. Eine Liste der Typnamen, finden Sie unter [zuordnen ein Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Verwenden Sie den Nachrichtenklassennamen von Outlook-Elementen im Assistenten **Neuer Outlook-Formularbereich** , um das Element dem Formularbereich zuzuordnen. Eine Liste der gültigen Nachrichtenklassennamen finden Sie [zuordnen ein Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="ReadingPane"></a> Entwerfen von benachbarten Formularbereichen für den Lesebereich
 Im Outlook-Lesebereich kann die Vorschau eines Outlook-Elements ohne Öffnen des Elements angezeigt werden. Der Lesebereich ist nur für Lesezwecke vorgesehen. Daher verhalten sich Eingabesteuerelemente, die Sie einem benachbarten Formularbereich hinzufügen (beispielsweise ein Textfeld), unter Umständen nicht wie erwartet, wenn das Element und der Formularbereich im Lesebereich geöffnet sind.

 Beispiel: Ist ein Element, das über einen benachbarten Formularbereich verfügt, im Lesebereich geöffnet, kann folgende Situation eintreten:

1. Wählen Sie in einem Textfeld, das sich im Formularbereich befindet, Text aus.

2. Drücken Sie **löschen**.

3. Anstelle des Texts im Textfeld wird das gesamte E-Mail-Element gelöscht.

   Wird ein benachbarter Formularbereich entworfen, der Eingabesteuerelemente beinhaltet, testen Sie die Steuerelemente im Lesebereich, um sicherzustellen, dass sie ordnungsgemäß funktionieren. Fügen Sie ggf. benutzerdefinierten Code hinzu, durch den Steuerelemente mit unerwartetem Verhalten deaktiviert werden.

   Sie können auch die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> -Eigenschaft des Formularbereichs auf **False**. Dadurch kann der Formularbereich nicht im Lesebereich verwendet werden.

## <a name="UsingOptimal"></a> Verwenden von optimalen Symbolgrößen
 Sie können angeben, welche Symbole im Formularbereich angezeigt werden sollen. Legen Sie dazu Symboleigenschaften in der Eigenschaftsgruppe **Symbole** des Fensters **Eigenschaften** fest. Verwenden Sie die folgenden Richtlinien, um die beste visuelle Qualität zu erzielen:

- Verwenden Sie für das **Seitensymbol** eine PNG-Datei (Portable Network Graphics).

- **Fenstersymbole** sollten eine Auflösung von 32 x 32 Pixel besitzen.

- Alle anderen Symbole sollten eine Auflösung von 16 x 16 Pixel besitzen.

  Das **Seitensymbol** wird auf dem Menüband eines Inspektors für Elemente angezeigt, die über folgende Formularbereiche verfügen: „Separat“, „Ersetzung“ oder „Alle ersetzen“.

  Die **Fenster** wird im Infobereich der Taskleiste und in der **Alt**+**Registerkarte** im Dialogfeld für offene Elemente, Anzeige Ersatz oder alle ersetzen Regionen.

## <a name="see-also"></a>Siehe auch
- [Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
