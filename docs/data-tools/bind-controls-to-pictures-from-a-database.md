---
title: "Gewusst wie: Binden von Steuerelementen an Bilder aus einer Datenbank | Microsoft Docs"
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
  - "Datenbindung [Windows Forms], Bilder"
  - "Datenquellenfenster, Festlegen von Steuerelementen für die Anzeige von Bildern"
  - "Bilder [Visual Basic], Datenbindung"
  - "Bilder [Visual Basic], Anzeigen in Windows Forms"
  - "Bilder [Visual Basic], Ziehen aus Datenquellenfenster"
  - "PictureBox-Steuerelement [Windows Forms], Datenbindung"
  - "Bilder, Datenbindung"
  - "Bilder, Ziehen aus Datenquellenfenster"
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Binden von Steuerelementen an Bilder aus einer Datenbank
Sie können im Datenquellenfenster ein Bild in einer Datenbank an ein Steuerelement in der Anwendung binden.  Zum Beispiel kann ein Bild an ein <xref:System.Windows.Controls.Image>\-Steuerelement in einer WPF\-Anwendung oder an ein <xref:System.Windows.Forms.PictureBox>\-Steuerelement in einer Windows Forms\-Anwendung gebunden werden.  
  
 Bilder in einer Datenbank werden in der Regel als Bytearrays gespeichert.  Für Elemente im Datenquellenfenster, die als Bytearrays gespeichert werden, wird der Steuerelementtyp standardmäßig auf **Keine** festgelegt, da Bytearrays sämtliche Objekte von einem einfachen Bytearray bis zur ausführbaren Datei einer großen Anwendung enthalten können.  Um für ein Bytearrayelement im Datenquellenfenster ein datengebundenes Steuerelement zu erstellen, das ein Bild darstellt, muss das zu erstellende Steuerelement ausgewählt werden.  
  
 In der folgenden Prozedur wird davon ausgegangen, dass das **Datenquellenfenster** bereits mit einem an das Bild gebundenen Element gefüllt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### So binden Sie ein Bild in einer Datenbank an ein Steuerelement  
  
1.  Stellen Sie sicher, dass die Entwurfsoberfläche, der Sie das Steuerelement hinzufügen möchten, im WPF\-Designer oder im Windows Forms\-Designer geöffnet ist.  
  
2.  Erweitern Sie im Datenquellenfenster die gewünschte Tabelle oder das gewünschte Objekt, sodass die Spalten bzw. Eigenschaften angezeigt werden.  
  
3.  Wählen Sie die Spalte oder die Eigenschaft aus, die die Bilddaten enthält, und wählen Sie eines der folgenden Steuerelemente aus der Dropdown\-Steuerelementliste aus:  
  
    -   Wenn der WPF\-Designer geöffnet ist, wählen Sie **Bild** aus.  
  
    -   Wenn der Windows Forms\-Designer geöffnet ist, wählen Sie **PictureBox** aus.  
  
    -   Sie können auch ein anderes Steuerelement auswählen, das die Datenbindung unterstützt und Bilder anzeigen kann.  Wenn das Steuerelement, das Sie verwenden möchten, nicht in der Liste der verfügbaren Steuerelemente enthalten ist, können Sie es der Liste hinzufügen und es anschließend auswählen.  Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Siehe auch  
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)