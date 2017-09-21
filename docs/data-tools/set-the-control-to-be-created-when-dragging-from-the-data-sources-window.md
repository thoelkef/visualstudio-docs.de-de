---
title: "Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Datenquellenfenster, Auswählen von Steuerelementen"
  - "Windows Forms, Anzeigen von Daten"
  - "Daten [Visual Studio], Anzeigen in Windows Forms"
  - "Daten [Visual Studio], Datenquellenfenster"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll
Sie können datengebundene Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** in den WPF\- oder den Windows Forms\-Designer ziehen.  Jedes Element im **Datenquellenfenster** verfügt über ein Standardsteuerelement, das erstellt wird, wenn Sie es in den Designer ziehen.  Sie können jedoch ein anderes Steuerelement erstellen.  
  
## Festlegen der Steuerelemente, die für Datentabellen oder Objekte erstellt werden sollen  
 Bevor Sie Elemente aus dem **Datenquellenfenster** ziehen, die Datentabellen oder Objekte darstellen, können Sie zwischen zwei Optionen wählen: Alle Daten können in einem Steuerelement oder jede Spalte bzw. Eigenschaft in einem separaten Steuerelement angezeigt werden.  
  
 In diesem Kontext bezieht sich der Begriff *Objekt* auf ein benutzerdefiniertes Geschäftsobjekt, eine Entität \(in einem Entity Data Model\) oder ein von einem Dienst zurückgegebenes Objekt.  
  
#### So legen Sie die Steuerelemente fest, die für Datentabellen oder Objekte erstellt werden sollen  
  
1.  Der WPF\- oder der Windows Forms\-Designer muss geöffnet sein.  
  
2.  Wählen Sie im **Datenquellenfenster** das Element aus, das die festzulegende Datentabelle oder das Objekt darstellt.  
  
3.  Klicken Sie auf das Dropdownmenü für das Element, und klicken Sie im Menü auf eines der folgenden Elemente:  
  
    -   Klicken Sie auf **Details**, um jedes Datenfeld in einem separaten Steuerelement anzuzeigen.  Wenn Sie das Datenelement in den Designer ziehen, werden für jede Spalte bzw. jede Eigenschaft der übergeordneten Datentabelle oder des Objekts ein anderes datengebundenes Steuerelement sowie Bezeichnungen für jedes Steuerelement erstellt.  
  
    -   Wählen Sie ein anderes Steuerelement in der Liste, z. B. **DataGrid** oder **List** in einer WPF\-Anwendung, oder **DataGridView** in einer Windows Forms\-Anwendung aus, um alle Daten in einem einzelnen Steuerelement anzuzeigen.  
  
     Die Liste der verfügbaren Steuerelemente hängt vom geöffneten Designer, der Version von .NET Framework, auf die das Projekt abzielt, und davon ab, ob Sie benutzerdefinierte Steuerelemente hinzugefügt haben, die die Datenbindung zur **Toolbox** unterstützen.  Wenn das gewünschte Steuerelement in der Liste der verfügbaren Steuerelemente aufgeführt ist, können Sie der Liste das Steuerelement hinzufügen.  Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Informationen dazu, wie ein benutzerdefiniertes Windows Forms\-Steuerelement erstellt wird, das der Liste der Steuerelemente für Datentabellen oder Objekte im **Datenquellenfenster** hinzugefügt werden kann, erhalten Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## Festlegen der Steuerelemente, die für Datenspalten oder \-eigenschaften erstellt werden sollen  
 Bevor Sie ein Element, das eine Spalte oder eine Eigenschaft eines Objekts im **Datenquellenfenster** darstellt, in den Designer ziehen, können Sie das zu erstellende Steuerelement festlegen.  
  
#### So legen Sie die Steuerelemente fest, die für Spalten oder Eigenschaften erstellt werden sollen  
  
1.  Der WPF\- oder der Windows Forms\-Designer muss geöffnet sein.  
  
2.  Erweitern Sie im **Datenquellenfenster** die gewünschte Tabelle oder das gewünschte Objekt, sodass die Spalten bzw. Eigenschaften angezeigt werden.  
  
3.  Wählen Sie jede Spalte oder jede Eigenschaft aus, für die das Steuerelement erstellt werden soll.  
  
4.  Klicken Sie auf das Dropdownmenü für die Spalte oder die Eigenschaft, und wählen Sie das Steuerelement aus, das beim Ziehen des Elements in den Designer erstellt werden soll.  
  
     Die Liste der verfügbaren Steuerelemente hängt vom geöffneten Designer, der Version von .NET Framework, auf die das Projekt abzielt, und davon ab, welche benutzerdefinierten Steuerelemente, die die Datenbindung zur **Toolbox** unterstützen, Sie hinzugefügt haben.  Wenn das gewünschte Steuerelement in der Liste der verfügbaren Steuerelemente aufgeführt ist, können Sie der Liste das Steuerelement hinzufügen.  Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Informationen dazu, wie ein benutzerdefiniertes Steuerelement erstellt wird, das der Liste der Steuerelemente für Datenspalten oder Eigenschaften im **Datenquellenfenster** hinzugefügt werden kann, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Wählen Sie im Dropdownmenü die Option **Keine** aus, wenn Sie kein Steuerelement für die Spalte oder Eigenschaft erstellen wollen.  Dies ist nützlich, wenn Sie die übergeordnete Tabelle oder das Objekt in den Designer ziehen, aber die Spalte oder die Eigenschaft nicht einschließen möchten.  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)