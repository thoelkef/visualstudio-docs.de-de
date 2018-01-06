---
title: "Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: ffa55100e9bbec33fdbca19ab2757c4de63f5030
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster
Beim Ziehen eines Elements aus der **Datenquellen** Fenster auf eine Entwurfsoberfläche zum Erstellen eines datengebundenen Steuerelements können Sie den Typ des von Ihnen erstellte Steuerelement auswählen. Jedes Element im Fenster verfügt über eine Dropdownliste, in dem die Steuerelemente angezeigt, aus denen Sie auswählen können. Der Satz von Steuerelementen, die jedes Element zugeordnet wird durch den Datentyp des Elements bestimmt. Wenn das Steuerelement, das Sie erstellen möchten, nicht in der Liste angezeigt wird, können Sie die Anweisungen in diesem Thema, um das Steuerelement zur Liste hinzufügen befolgen.  
  
 Weitere Informationen zum Auswählen von datengebundenen Steuerelementen zum Erstellen für Elemente in der **Datenquellen** Fenster finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. So ändern Sie die Einstellungen für die **Tools** klicken Sie im Menü **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
##  <a name="customizinglist"></a>Anpassen der Liste der bindungsfähige Steuerelemente für einen-Datentyp  
 Zum Hinzufügen oder Entfernen von Steuerelementen aus der Liste der verfügbaren Steuerelemente für Elemente in der **Datenquellen** Fenster, das über einen bestimmten Datentyp, der die folgenden Schritte ausführen.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Wählen Sie die Steuerelemente für einen-Datentyp aufgelistet werden  
  
1.  Stellen Sie sicher, dass der WPF- oder Windows Forms-Designer geöffnet ist.  
  
2.  In der **Datenquellen** Fenster, klicken Sie auf ein Element, das Bestandteil einer Datenquelle, die Sie hinzugefügt, um das Fenster haben ist, und klicken Sie dann auf das Dropdownmenü für das Element.  
  
3.  Klicken Sie in der Dropdown-Menü auf **anpassen**. Einer der folgenden Dialogfelder geöffnet:  
  
    -   Wenn die Windows Forms-Designer geöffnet ist, wird die **Datenbenutzeroberfläche** auf der Seite der **Optionen** Dialogfeld wird geöffnet.  
  
    -   Wenn der WPF-Designer geöffnet ist, wird die **anpassen Steuerelement binden** Dialogfeld wird geöffnet.  
  
4.  Wählen Sie im Dialogfeld einen Datentyp aus der **Datentyp** Dropdown-Liste.  
  
    -   Wählen Sie zum Anpassen der Liste der Steuerelemente für eine Tabelle oder ein Objekt **[Liste]**.  
  
    -   Um die Liste der Steuerelemente für eine Spalte einer Tabelle oder eine Eigenschaft eines Objekts anzupassen, wählen Sie den Datentyp der Spalte oder Eigenschaft im zugrunde liegenden Datenspeicher.  
  
    -   Wählen Sie zum Anpassen der Liste der Steuerelemente zum Anzeigen von Datenobjekte, die eine benutzerdefinierte Formen besitzen **[andere]**. Wählen Sie z. B. **[andere]** verfügt Ihre Anwendung ein benutzerdefiniertes Steuerelement, das Daten aus mehr als eine Eigenschaft eines bestimmten Objekts anzeigt.  
  
5.  In der **zugeordnete Steuerelemente** Feld, wählen Sie jedes Steuerelement, das Sie für den ausgewählten Datentyp verfügbar sein sollen, oder heben Sie die Auswahl aller Steuerelemente, die Sie aus der Liste entfernen möchten.  
  
    > [!NOTE]
    >  Wenn das Steuerelement, das Sie auswählen möchten nicht, in angezeigt wird der **zugeordnete Steuerelemente** Feld müssen Sie das Steuerelement zur Liste hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zur Liste der zugeordneten Steuerelemente für einen Datentyp](#addingcontrols).  
  
6.  Klicken Sie auf **OK**.  
  
7.  In der **Datenquellen** Fenster, klicken Sie auf ein Element der Daten geben, dass Sie nur ein oder mehrere Steuerelemente verknüpft, und klicken Sie dann auf das Dropdownmenü für das Element.  
  
     Die Steuerelemente, die Sie ausgewählt haben, in der **zugeordnete Steuerelemente** Feld jetzt in der Dropdown-Menü für das Element angezeigt werden.  
  
##  <a name="addingcontrols"></a>Hinzufügen von Steuerelementen zur Liste der zugeordneten Steuerelemente für einen-Datentyp  
 Wenn ein Steuerelement mit einem Datentyp zugeordnet werden soll, aber das Steuerelement nicht in erscheint der **zugeordnete Steuerelemente** Feld, müssen Sie der Liste das Steuerelement hinzufügen. Das Steuerelement muss in der aktuellen Projektmappe oder in einer referenzierten Assembly befinden. Muss auch verfügbar sein, in der **Toolbox**, und haben ein Attribut, das Steuerelement Datenbindungsverhalten angibt.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Die Liste der zugeordneten Steuerelemente Steuerelemente hinzu  
  
1.  Fügen Sie das gewünschte Steuerelement auf die **Toolbox** durch Rechtsklick auf die **Toolbox** auswählen und **Elemente auswählen**.  
  
     Das Steuerelement muss einen der folgenden Attribute aufweisen.  
  
    |Attribut|Beschreibung|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementieren Sie dieses Attribut für einfache Steuerelemente, die eine einzelne Spalte (oder Eigenschaft) von Daten anzeigen, wie z. B. eine <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementieren Sie dieses Attribut auf Steuerelemente zur Anzeige von Listen (oder Tabellen) von Daten, z. B. eine <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementieren Sie dieses Attribut auf Steuerelemente zur Anzeige von Listen (oder Tabellen) von Daten, sondern auch eine einzelne Spalte oder Eigenschaft darstellen müssen, z. B. eine <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Für Windows Forms auf die **Optionen** öffnen Sie im Dialogfeld die **Datenbenutzeroberfläche** Seite. Für WPF, öffnen Sie alternativ die **anpassen Steuerelement binden** (Dialogfeld). Weitere Informationen finden Sie unter [Anpassen der Liste der bindungsfähige Steuerelemente für einen Datentyp](#customizinglist).  
  
3.  In der **zugeordnete Steuerelemente** Feld, das Steuerelement, das Sie gerade hinzugefügt haben die **Toolbox** sollte jetzt angezeigt werden.  
  
    > [!NOTE]
    >  Nur die folgenden Steuerelemente, die sich innerhalb der aktuellen Projektmappe oder in einer referenzierten Assembly befinden können die Liste der zugeordneten Steuerelemente hinzugefügt werden. (Die Steuerelemente müssen auch eines der Attribute für die Datenbindung in der obigen Tabelle implementieren.) Um Daten an ein benutzerdefiniertes Steuerelement zu binden, die in nicht verfügbar ist die **Datenquellen** Fenster ziehen Sie das Steuerelement aus der **Toolbox** auf die Entwurfsoberfläche, und ziehen Sie dann das Element, das aus Binden der **Daten Quellen** Fenster auf das Steuerelement.  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)