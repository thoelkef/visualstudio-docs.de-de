---
title: Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellen Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 402e62602d99492730d3094965e76964cd5f8218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673096"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie ein Element aus dem **Datenquellen** Fenster auf eine Entwurfs Oberfläche ziehen, um ein Daten gebundenes Steuerelement zu erstellen, können Sie den Typ des Steuer Elements auswählen, das Sie erstellen. Jedes Element im-Fenster verfügt über eine Dropdown Liste, in der die Steuerelemente angezeigt werden, aus denen Sie auswählen können. Der Satz von Steuerelementen, die jedem Element zugeordnet sind, wird durch den Datentyp des Elements bestimmt. Wenn das Steuerelement, das Sie erstellen möchten, nicht in der Liste angezeigt wird, können Sie die Anweisungen in diesem Thema befolgen, um der Liste das Steuerelement hinzuzufügen.

 Weitere Informationen zum Auswählen von Daten gebundenen Steuerelementen, die für Elemente im **Datenquellen** Fenster erstellt werden sollen, finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Um die Einstellungen zu ändern, wählen **Sie im Menü Extras die Option** **Einstellungen importieren und exportieren**aus. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="customize-the-list-of-bindable-controls-for-a-data-type"></a><a name="customizinglist"></a> Anpassen der Liste der bindbaren Steuerelemente für einen Datentyp
 Zum Hinzufügen oder Entfernen von Steuerelementen aus der Liste der verfügbaren Steuerelemente für Elemente im **Datenquellen** Fenster, die einen bestimmten Datentyp aufweisen, führen Sie die folgenden Schritte aus.

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>So wählen Sie die Steuerelemente aus, die für einen Datentyp aufgelistet werden sollen

1. Der WPF- oder der Windows Forms-Designer muss geöffnet sein.

2. Klicken Sie im Fenster **Datenquellen** auf ein Element, das Teil einer Datenquelle ist, die Sie dem-Fenster hinzugefügt haben, und klicken Sie dann auf das Dropdown Menü für das Element.

3. Klicken Sie im Dropdown Menü auf **Anpassen**. Eines der folgenden Dialogfelder wird geöffnet:

    - Wenn das Windows Forms-Designer geöffnet ist, wird die Seite **Daten Anpassung der Benutzeroberfläche** des Dialog Felds **Optionen** geöffnet.

    - Wenn der WPF-Designer geöffnet ist, wird das Dialogfeld **Steuerelement Bindung anpassen** geöffnet.

4. Wählen Sie im Dialogfeld in der Dropdown Liste **Datentyp** einen Datentyp aus.

    - Wählen Sie **[list]** aus, um die Liste der Steuerelemente für eine Tabelle oder ein Objekt anzupassen.

    - Wählen Sie den Datentyp der Spalte oder Eigenschaft im zugrunde liegenden Datenspeicher aus, um die Liste der Steuerelemente für eine Spalte einer Tabelle oder eine Eigenschaft eines Objekts anzupassen.

    - Zum Anpassen der Liste der Steuerelemente zum Anzeigen von Datenobjekten, die benutzerdefinierte Formen aufweisen, wählen Sie **[Other]** aus. Wählen Sie z. b. **[Other]** aus, wenn Ihre Anwendung über ein benutzerdefiniertes Steuerelement verfügt, das Daten aus mehr als einer Eigenschaft eines bestimmten Objekts anzeigt.

5. Wählen Sie im Feld zugeordnete Steuer **Elemente** die einzelnen Steuerelemente aus, die für den ausgewählten Datentyp verfügbar sein sollen, oder deaktivieren Sie die Auswahl aller Steuerelemente, die Sie aus der Liste entfernen möchten.

    > [!NOTE]
    > Wenn das Steuerelement, das Sie auswählen möchten, nicht im Feld zugeordnete Steuer **Elemente** angezeigt wird, müssen Sie das Steuerelement der Liste hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zur Liste der zugeordneten Steuerelemente für einen Datentyp](#addingcontrols).

6. Klicken Sie auf **OK**.

7. Klicken Sie im **Datenquellen** Fenster auf ein Element des Datentyps, dem Sie soeben mindestens ein Steuerelement zugeordnet haben, und klicken Sie dann auf das Dropdown Menü für das Element.

     Die Steuerelemente, die Sie im Feld zugeordnete Steuer **Elemente** ausgewählt haben, werden jetzt im Dropdown Menü für das Element angezeigt.

## <a name="addcontrols-to-the-list-of-associated-controls-for-a-data-type"></a><a name="addingcontrols"></a> Addcontrols zur Liste der zugeordneten Steuerelemente für einen Datentyp
 Wenn Sie ein Steuerelement einem Datentyp zuordnen möchten, das Steuerelement jedoch nicht im Feld zugeordnete Steuer **Elemente** angezeigt wird, müssen Sie das Steuerelement der Liste hinzufügen. Das-Steuerelement muss sich in der aktuellen Projekt Mappe oder in einer Assembly befinden, auf die verwiesen wird. Außerdem muss Sie in der **Toolbox**verfügbar sein und über ein Attribut verfügen, das das Daten Bindungsverhalten des Steuer Elements angibt.

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>So fügen Sie der Liste der zugeordneten Steuerelemente Steuerelemente hinzu

1. Fügen Sie das gewünschte Steuerelement der **Toolbox** hinzu, indem Sie mit der rechten Maustaste auf die **Toolbox** klicken und **Elemente auswählen**auswählen.

     Das Steuerelement muss eines der folgenden Attribute aufweisen.

    |attribute|BESCHREIBUNG|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementieren Sie dieses Attribut für einfache Steuerelemente, die eine einzelne Spalte (oder Eigenschaft) von Daten anzeigen, z <xref:System.Windows.Forms.TextBox> . b..|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementieren Sie dieses Attribut für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, z <xref:System.Windows.Forms.DataGridView> . b..|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementieren Sie dieses Attribut für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft, z. b. eine, darstellen müssen <xref:System.Windows.Forms.ComboBox> .|

2. Öffnen Sie für Windows Forms im Dialogfeld      **Optionen** die Seite **Anpassung der Daten Benutzeroberfläche** . Oder öffnen Sie für WPF das Dialogfeld **Steuerelement Bindung anpassen** . Weitere Informationen finden Sie unter [Anpassen der Liste der bindbaren Steuerelemente für einen-Datentyp](#customizinglist).

3. Im Feld zugeordnete Steuer **Elemente** sollte das Steuerelement, das Sie soeben der **Toolbox** hinzugefügt haben, nun angezeigt werden.

    > [!NOTE]
    > Nur Steuerelemente, die sich innerhalb der aktuellen Projekt Mappe oder in einer referenzierten Assembly befinden, können der Liste der zugeordneten Steuerelemente hinzugefügt werden. (Die Steuerelemente müssen auch eines der Daten Bindungs Attribute in der vorherigen Tabelle implementieren.) Zum Binden von Daten an ein benutzerdefiniertes Steuerelement, das im **Datenquellen** Fenster nicht verfügbar ist, ziehen Sie das Steuerelement aus der **Toolbox** auf die Entwurfs Oberfläche, und ziehen Sie dann das Element, an das die Bindung erfolgen soll, aus dem **Datenquellen** Fenster auf das Steuerelement.

## <a name="see-also"></a>Weitere Informationen
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
