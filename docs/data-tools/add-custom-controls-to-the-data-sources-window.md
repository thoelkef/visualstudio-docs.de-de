---
title: Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b4cd6004519573064683d87a35d1b3c49711edb6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867932"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster

Beim Ziehen eines Elements aus der **Datenquellen** Fenster auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements können Sie den Typ des von Ihnen erstellte Steuerelement auswählen. Jedes Element in das Fenster verfügt über eine Dropdownliste, in dem die Steuerelemente angezeigt, denen Sie auswählen können. Der Satz von Steuerelementen, die jedem Element wird durch den Datentyp des Elements bestimmt. Wenn das Steuerelement, das Sie erstellen möchten, nicht in der Liste angezeigt wird, können Sie die Anweisungen in diesem Thema, um das Steuerelement zur Liste hinzuzufügen befolgen.

Weitere Informationen zum Auswählen von datengebundenen Steuerelementen für die Erstellung für Elemente in der **Datenquellen** Fenster finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Anpassen der Liste bindungsfähige Steuerelemente

Zum Hinzufügen oder entfernen Steuerelemente aus der Liste der verfügbaren Steuerelemente für Elemente in der **Datenquellen** Fenster, das einen bestimmten Datentyp, der die folgenden Schritte ausführen zu müssen.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Die Steuerelemente für einen Datentyp aufgeführt werden auswählen

1. Der WPF- oder der Windows Forms-Designer muss geöffnet sein.

2. In der **Datenquellen** , klicken Sie auf ein Element, das ist Teil einer Datenquelle, die Sie hinzugefügt, um das Fenster haben, und klicken Sie dann auf das Dropdownmenü für das Element.

   > [!TIP]
   > Wenn die **Datenquellen** Fenster nicht geöffnet ist, öffnen Sie es durch Auswählen von **Ansicht** > **Other Windows** > **Datenquellen**.

3. Klicken Sie im Dropdown-Menü auf **anpassen**. Eine der folgenden Dialogfelder geöffnet:

    - Wenn die **Windows Forms-Designer** geöffnet ist, die **Daten für die Benutzeroberflächenanpassung** auf der Seite die **Optionen** Dialogfeld wird geöffnet.

    - Wenn die **WPF-Designer** geöffnet ist, die **Steuerelementbindung anpassen** Dialogfeld wird geöffnet.

4. Wählen Sie im Dialogfeld, einen Datentyp aus der **Datentyp** Dropdown-Liste.

    - Wählen Sie zum Anpassen der Liste der Steuerelemente für eine Tabelle oder ein Objekt **[List]**.

    - Um die Liste der Steuerelemente für eine Spalte einer Tabelle oder eine Eigenschaft eines Objekts anzupassen, wählen Sie den Datentyp der Spalte oder Eigenschaft in den zugrunde liegenden Datenspeicher.

    - Wählen Sie zum Anpassen der Liste der Steuerelemente zum Anzeigen von Datenobjekten, die eine benutzerdefinierte Formen **[andere]**. Wählen Sie z. B. **[andere]** verfügt Ihre Anwendung ein benutzerdefiniertes Steuerelement, das Daten aus mehr als eine Eigenschaft eines bestimmten Objekts anzeigt.

5. In der **zugeordnete Steuerelemente** wählen jedes Steuerelement, das Sie für den ausgewählten Datentyp verfügbar sein soll, oder heben Sie die Auswahl aller Steuerelemente, die Sie aus der Liste entfernen möchten.

    > [!NOTE]
    > Wenn das Steuerelement, das Sie auswählen möchten nicht, in angezeigt wird der **zugeordnete Steuerelemente** Feld müssen Sie das Steuerelement zur Liste hinzufügen. Weitere Informationen finden Sie unter [fügen Sie Steuerelemente zugeordnete](#add-associated-controls).

6. Klicken Sie auf **OK**.

7. In der **Datenquellen** Fenster, die auf ein Element der Daten, dem ein oder mehrere Steuerelemente zugeordnet, und klicken Sie dann auf das Dropdownmenü für das Element.

     Die Steuerelemente, die Sie, in ausgewählt der **zugeordnete Steuerelemente** jetzt in der Dropdown-Menü für das Element angezeigt.

## <a name="add-associated-controls"></a>Zugeordnete Steuerelemente hinzufügen

Wenn ein Steuerelement mit einem Datentyp zugeordnet werden soll, aber das Steuerelement nicht, in angezeigt wird der **zugeordnete Steuerelemente** Feld müssen Sie das Steuerelement zur Liste hinzufügen. Das Steuerelement muss sich in der aktuellen Projektmappe oder in einer referenzierten Assembly sein. Auch in verfügbar sein muss die **Toolbox** und über ein Attribut, das Datenbindungsverhalten des Steuerelements angibt.

### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Die Liste der zugehörigen Steuerelemente Steuerelemente hinzu

1. Fügen Sie das gewünschte Steuerelement auf der **Toolbox** mit der rechten Maustaste die **Toolbox** und **Elemente auswählen**.

     Das Steuerelement muss es sich um einen der folgenden Attribute aufweisen.

    |Attribut|Beschreibung|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementieren Sie dieses Attribut für einfache Steuerelemente, die eine einzelne Spalte (oder Eigenschaft) der Daten anzeigen, wie z. B. eine <xref:System.Windows.Forms.TextBox>.|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementieren Sie dieses Attribut auf Steuerelemente zum Anzeigen von Listen (oder Tabellen) von Daten, z. B. eine <xref:System.Windows.Forms.DataGridView>.|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementieren Sie dieses Attribut auf Steuerelemente zum Anzeigen von Listen (oder Tabellen) von Daten, sondern auch eine einzelne Spalte oder Eigenschaft darstellen müssen, z. B. eine <xref:System.Windows.Forms.ComboBox>.|

2. Für Windows Forms auf die **Optionen** öffnen Sie im Dialogfeld die **Daten für die Benutzeroberflächenanpassung** Seite. Für WPF, öffnen Sie alternativ die **Steuerelementbindung anpassen** Dialogfeld. Weitere Informationen finden Sie unter [anpassen die Liste der bindungsfähige Steuerelemente für einen Datentyp](#customize-the-bindable-controls-list).

3. In der **zugeordnete Steuerelemente** Feld, das Steuerelement, das Sie gerade hinzugefügt haben, um die **Toolbox** sollte jetzt angezeigt werden.

    > [!NOTE]
    > Nur Steuerelemente, die sich innerhalb der aktuellen Projektmappe oder in einer referenzierten Assembly befinden, können die Liste mit den zugehörigen Steuerelementen hinzugefügt werden. (Die Steuerelemente müssen auch eines der Attribute für die Datenbindung in der vorherigen Tabelle implementieren.) Um Daten an ein benutzerdefiniertes Steuerelement zu binden, die in nicht verfügbar ist die **Datenquellen** Fenster ziehen Sie das Steuerelement aus der **Toolbox** auf der Entwurfsoberfläche, und ziehen Sie dann das Element, das aus binden die **Daten Quellen** Fenster auf das Steuerelement.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)