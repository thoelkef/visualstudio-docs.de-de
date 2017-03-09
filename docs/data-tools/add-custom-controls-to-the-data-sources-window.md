---
title: "Hinzuf&#252;gen benutzerdefinierter Steuerelemente zum Datenquellenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Datenquellenfenster, Hinzufügen von Steuerelementen"
  - "Steuerelemente [Visual Studio], Hinzufügen zum Datenquellenfenster"
  - "DefaultBindingPropertyAttribute-Klasse, verwenden"
  - "LookupBindingPropertiesAttribute-Klasse, verwenden"
  - "ComplexBindingPropertiesAttribute-Klasse, verwenden"
  - "Datenquellenfenster, Auswählen von Steuerelementen"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hinzuf&#252;gen benutzerdefinierter Steuerelemente zum Datenquellenfenster
Wenn Sie ein Element aus einem **Datenquellenfenster** in eine Designoberfläche ziehen, um ein datengebundenes Steuerelement zu erstellen, können Sie den Typ des Steuerelements auswählen, das Sie erstellen.  Jedes Element im Fenster weist eine Dropdownliste auf, die die auswählbaren Steuerelemente anzeigt.  Die den einzelnen Elementen zugeordneten Steuerelemente werden vom Datentyp des Elements bestimmt.  Wenn das gewünschte Steuerelement nicht in der Liste angezeigt wird, folgen Sie den Anweisungen in diesem Thema, um so das Steuerelement der Liste hinzuzufügen.  
  
 Weitere Informationen zum Auswählen von datengebundenen Steuerelementen, die für Elemente im **Datenquellenfenster** erstellt werden sollen, finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Um die Einstellungen zu ändern, wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Anpassen der Liste bindungsfähiger Steuerelemente für einen Datentyp  
 Führen Sie die folgenden Schritte aus, um Steuerelemente aus der Liste der verfügbaren Steuerelemente für Elemente im **Datenquellenfenster** hinzuzufügen oder zu entfernen, die einen bestimmten Datentyp aufweisen.  
  
#### So wählen Sie die für einen Datentyp aufzulistenden Steuerelemente aus  
  
1.  Der WPF\-Designer oder der Windows Forms\-Designer muss geöffnet sein.  
  
2.  Klicken Sie im **Datenquellenfenster** auf ein Element, das Teil einer dem Fenster hinzugefügten Datenquelle ist, und klicken Sie dann auf das Dropdownmenü für das Element.  
  
3.  Klicken Sie im Dropdownmenü auf **Anpassen**.  Eines der folgenden Dialogfelder wird geöffnet:  
  
    -   Wenn der Windows Forms\-Designer geöffnet ist, wird die Seite **Anpassung der Datenbenutzeroberfläche** des Dialogfelds **Optionen** geöffnet.  
  
    -   Wenn der WPF\-Designer geöffnet ist, wird das Dialogfeld **Steuerelementbindung anpassen** geöffnet.  
  
4.  Wählen Sie im Dialogfeld einen Datentyp aus der Dropdownliste **Datentyp** aus.  
  
    -   Wählen Sie **\[Liste\]** aus, um die Liste der Steuerelemente für eine Tabelle oder ein Objekt anzupassen.  
  
    -   Zum Anpassen der Liste der Steuerelemente für eine Spalte einer Tabelle oder eine Eigenschaft eines Objekts wählen Sie den Datentyp der Spalte oder Eigenschaft im zugrunde liegenden Datenspeicher aus.  
  
    -   Wählen Sie **\[Andere\]** aus, um die Liste der Steuerelemente so anzupassen, dass Datenobjekte mit benutzerdefinierten Formen angezeigt werden.  Wenn die Anwendung z. B. ein benutzerdefiniertes Steuerelement enthält, das Daten von mehreren Objekteigenschaften eines bestimmten Objekts anzeigt, wählen Sie **\[Andere\]** aus.  
  
5.  Wählen Sie im Feld **Zugeordnete Steuerelemente** die einzelnen Steuerelemente aus, die für den ausgewählten Datentyp verfügbar sein sollen, oder heben Sie die Auswahl aller Steuerelemente auf, die aus der Liste entfernt werden sollen.  
  
    > [!NOTE]
    >  Wenn das gewünschte Steuerelement nicht im Feld **Zugeordnete Steuerelemente** angezeigt wird, müssen Sie der Liste das Steuerelement hinzufügen.  Weitere Informationen finden Sie in [Hinzufügen von Steuerelementen zur Liste der zugeordneten Steuerelemente für einen Datentyp](#addingcontrols).  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie im **Datenquellenfenster** auf ein Element des Datentyps, dem mindestens ein Steuerelement zugeordnet wurde, und klicken Sie dann auf das Dropdownmenü für das Element.  
  
     Die im Feld **Zugeordnete Steuerelemente** ausgewählten Steuerelemente werden jetzt im Dropdownmenü des Elements angezeigt.  
  
##  <a name="addingcontrols"></a> Hinzufügen von Steuerelementen zur Liste der zugeordneten Steuerelemente für einen Datentyp  
 Wenn Sie einem Datentyp ein Steuerelement zuordnen möchten, aber das Steuerelement nicht im Feld **Zugeordnete Steuerelemente** angezeigt wird, müssen Sie der Liste das Steuerelement hinzufügen.  Das Steuerelement muss sich in der aktuellen Projektmappe oder einer Assembly, auf die verwiesen wird, befinden, in der **Toolbox** verfügbar sein und ein Attribut aufweisen, das das Datenbindungsverhalten des Steuerelements angibt.  
  
#### So fügen Sie Steuerelemente zur Liste der zugeordneten Steuerelemente hinzu  
  
1.  Fügen Sie das gewünschte Steuerelement zur **Toolbox** hinzu, indem Sie mit der rechten Maustaste auf die **Toolbox** klicken und **Elemente auswählen** auswählen.  
  
     Das Steuerelement muss eines der folgenden Attribute aufweisen.  
  
    |Attribut|Description|  
    |--------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementieren Sie dieses Attribut für einfache Steuerelemente, mit denen eine einzelne Spalte \(oder Eigenschaft\) angezeigt wird, z. B. eine <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementieren Sie dieses Attribut für Steuerelemente, mit denen Listen \(oder Tabellen\) von Daten angezeigt werden, z. B. eine <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementieren Sie dieses Attribut für Steuerelemente, mit denen Listen \(oder Tabellen\) von Daten angezeigt werden, die aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, z. B. eine <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Öffnen Sie im Dialogfeld **Optionen** \(Windows Forms\) die Seite **Anpassung der Datenbenutzeroberfläche** bzw. öffnen Sie das Dialogfeld \(WPF\) **Steuerelementbindung anpassen**.  Weitere Informationen finden Sie in [Anpassen der Liste bindungsfähiger Steuerelemente für einen Datentyp](#customizinglist).  
  
3.  Das zur **Toolbox** hinzugefügte Steuerelement, wird jetzt im Feld **Zugeordnete Steuerelemente** angezeigt.  
  
    > [!NOTE]
    >  Nur Steuerelemente, die sich in der aktuellen Projektmappe oder in einer Assembly befinden, auf die verwiesen wird \(und die eines der Datenbindungsattribute in der obigen Tabelle implementieren\), können der Liste der zugeordneten Steuerelemente hinzugefügt werden.  Wenn Sie Daten an ein benutzerdefiniertes Steuerelement binden möchten, das nicht im **Datenquellenfenster** verfügbar ist, ziehen Sie das Steuerelement aus der **Toolbox** auf die Designoberfläche, und ziehen Sie anschließend das Element, an das gebunden werden soll, aus dem **Datenquellenfenster** auf das benutzerdefinierte Steuerelement.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Dialogfeld "Steuerelementbindung anpassen"](../data-tools/customize-control-binding-dialog-box.md)