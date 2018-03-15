---
title: Richtlinien zum Erstellen von Outlook-Formularbereichen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 1e82a4428dde7aa25c7e9a3d7d74017b9f2a874f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Richtlinien zum Erstellen von Outlook-Formularbereichen
  Anhand der folgenden Informationen können Formularbereiche optimiert und mögliche Probleme vermieden werden:  
  
-   [Verwenden von Formularbereichsnamen](#UsingFormRegions).  
  
-   [Deaktivieren von Formularbereichsvererbung](#DisablingInheritance).  
  
-   [Grundlegendes zu Typen und Nachrichtenklassennamen](#ClassNames).  
  
-   [Entwerfen von benachbarten Formularbereichen für den Lesebereich](#ReadingPane).  
  
-   [Verwenden von optimalen Symbolgrößen](#UsingOptimal).  
  
 Weitere Informationen zu Formularbereichen finden Sie unter [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Using Form Region Names  
 Der Formularbereich wird mit mehreren Namen beschrieben. Es ist wichtig, den Unterschied zwischen diesen Namen und den jeweiligen Einfluss auf den Formularbereich zu kennen. In der folgenden Tabelle wird jeder Name beschrieben.  
  
|Formularbereichsname|Beschreibung|  
|----------------------|-----------------|  
|Formularbereichs-Elementname|Der Name, den Sie für das **Outlook-Formularbereich** -Element im Dialogfeld **Neues Element hinzufügen** angeben. Dies ist der Name der Formularbereich-Codedatei, die im **Projektmappen-Explorer**angezeigt wird.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> -Eigenschaft|Dieser Name wird auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** des Assistenten **Neuer Outlook-Formularbereich** angegeben. Dieser Name wird als **FormRegionName** -Eigenschaft im Fenster **Eigenschaften** angezeigt.<br /><br /> Verwenden Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> -Eigenschaft, um die Bezeichnung anzugeben, durch die der Formularbereich in der Outlook-Benutzeroberfläche identifiziert wird. In separaten Formularbereichen wird dieser Name als Schaltfläche auf dem Menüband des Outlook-Elements angezeigt.<br /><br /> In benachbarten Formularbereichen wird dieser Name als Headertext über dem Formularbereich angezeigt.|  
|Microsoft.Office.Tools.Outlook.FormRegionName-Attribut|Wird dem Projekt ein **Outlook-Formularbereich** -Element hinzugefügt, legt Visual Studio diese Eigenschaft auf den vollqualifizierten Namen des Formularbereichs fest. Der standardmäßige vollqualifizierte Name ist der Name des VSTO-Add-Ins, das durch einen Punkt mit dem Namen des Formularbereichs verbunden ist (beispielsweise `OutlookAddIn1.FormRegion1`).<br /><br /> Dieser vollqualifizierte Name wird am Anfang der Factoryklasse für den Formularbereich auch als Attribut angezeigt.<br /><br /> Verwenden Sie die Microsoft.Office.Tools.Outlook.FormRegionName-Attribut, um den Formularbereich in allen Outlook-VSTO-Add-ins eindeutig zu identifizieren. Durch Umbenennen des Formularbereichs oder durch ändern, ändern Sie den Wert des Attributs Microsoft.Office.Tools.Outlook.FormRegionName kann nicht die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Eigenschaft. Um diesen Namen zu ändern, müssen Sie das Microsoft.Office.Tools.Outlook.FormRegionName-Attribut in der Formularbereich-Codedatei ändern.|  
  
##  <a name="DisablingInheritance"></a> Disabling Form Region Inheritance  
 Standardmäßig erbt eine benutzerdefinierte Nachrichtenklasse alle Formularbereichzuordnungen der Basisnachrichtenklasse. Z. B. eine Nachrichtenklasse mit dem Namen `IPM.Task.Contoso` IPM abgeleitet. Aufgabe. Aus diesem Grund `IPM.Task.Contoso` formularbereichzuordnungen IPM erbt. Aufgabe.  
  
 Soll der Formularbereich abgeleiteten Nachrichtenklassen zugeordnet werden, legen Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> -Eigenschaft des Formularbereichs auf **true**. Beispielsweise, wenn Sie einen benachbarter Formularbereich IPM zuordnen. Aufgabe aus, und legen Sie die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> Eigenschaft, um **"true"**, die vom Formularbereich nur an das Ende einer standardmäßigen Aufgabenformulars angehängt. Der Formularbereich wird nicht an den unteren Bereich von angepassten Versionen eines standardmäßigen Aufgabenformulars angehängt.  
  
##  <a name="ClassNames"></a> Grundlegendes zu Typen und Nachrichtenklassennamen  
 Der Typname eines Outlook-Elements unterscheidet sich vom Namen der Nachrichtenklasse eines Outlook-Elements. Beispielsweise ist der Typname eines RSS-Elements Microsoft.Office.Interop.Outlook.PostItem. Der Klassenname der Nachricht ein RSS-Elements ist IPM. Post.RSS.  
  
 Verwenden Sie den Typnamen, um auf ein Outlook-Element in Code zu verweisen. Eine Liste der Typnamen finden Sie unter [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Verwenden Sie den Nachrichtenklassennamen von Outlook-Elementen im Assistenten **Neuer Outlook-Formularbereich** , um das Element dem Formularbereich zuzuordnen. Eine Liste der gültigen Nachrichtenklassennamen finden Sie unter [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Designing Adjoining Form Regions for the Reading Pane  
 Im Outlook-Lesebereich kann die Vorschau eines Outlook-Elements ohne Öffnen des Elements angezeigt werden. Der Lesebereich ist nur für Lesezwecke vorgesehen. Daher verhalten sich Eingabesteuerelemente, die Sie einem benachbarten Formularbereich hinzufügen (beispielsweise ein Textfeld), unter Umständen nicht wie erwartet, wenn das Element und der Formularbereich im Lesebereich geöffnet sind.  
  
 Beispiel: Ist ein Element, das über einen benachbarten Formularbereich verfügt, im Lesebereich geöffnet, kann folgende Situation eintreten:  
  
1.  Wählen Sie in einem Textfeld, das sich im Formularbereich befindet, Text aus.  
  
2.  Drücken Sie ENTF.  
  
3.  Anstelle des Texts im Textfeld wird das gesamte E-Mail-Element gelöscht.  
  
 Wird ein benachbarter Formularbereich entworfen, der Eingabesteuerelemente beinhaltet, testen Sie die Steuerelemente im Lesebereich, um sicherzustellen, dass sie ordnungsgemäß funktionieren. Fügen Sie ggf. benutzerdefinierten Code hinzu, durch den Steuerelemente mit unerwartetem Verhalten deaktiviert werden.  
  
 Sie können auch die <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> -Eigenschaft des Formularbereichs auf **False**. Dadurch kann der Formularbereich nicht im Lesebereich verwendet werden.  
  
##  <a name="UsingOptimal"></a> Using Optimal Icon Sizes  
 Sie können angeben, welche Symbole im Formularbereich angezeigt werden sollen. Legen Sie dazu Symboleigenschaften in der Eigenschaftsgruppe **Symbole** des Fensters **Eigenschaften** fest. Verwenden Sie die folgenden Richtlinien, um die beste visuelle Qualität zu erzielen:  
  
-   Verwenden Sie für das **Seitensymbol** eine PNG-Datei (Portable Network Graphics).  
  
-   **Fenstersymbole** sollten eine Auflösung von 32 x 32 Pixel besitzen.  
  
-   Alle anderen Symbole sollten eine Auflösung von 16 x 16 Pixel besitzen.  
  
 Das **Seitensymbol** wird auf dem Menüband eines Inspektors für Elemente angezeigt, die über folgende Formularbereiche verfügen: „Separat“, „Ersetzung“ oder „Alle ersetzen“.  
  
 Das **Fenstersymbol** wird im Benachrichtigungsbereich und im ALT+TAB-Dialogfeld für geöffnete Elemente angezeigt, die die Formularbereiche „Ersetzung“ oder „Alle ersetzen“ anzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  