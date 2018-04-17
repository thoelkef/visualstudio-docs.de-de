---
title: Binden von Steuerelementen an Bilder aus einer Datenbank | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 29d902f16051bd04079115baf87e33ac49d77396
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Binden von Steuerelementen an Bilder aus einer Datenbank
Können Sie die **Datenquellen** Fenster aus, um ein Bild in einer Datenbank an ein Steuerelement in der Anwendung zu binden. Sie können z. B. ein Bild zum Binden einer <xref:System.Windows.Controls.Image> steuern in einer WPF-Anwendung oder auf eine <xref:System.Windows.Forms.PictureBox> -Steuerelement in Windows Forms-Anwendung.  
  
Bilder in einer Datenbank werden in der Regel als Bytearrays gespeichert. Elemente in der **Datenquellen** Fenster, das als Bytearrays Steuerelementtyp haben gespeichert sind, legen Sie auf **keine** standardmäßig, da Bytearrays sämtliche Objekte von einem einfachen Bytearray bis zur ausführbaren Datei enthalten können einer großen Anwendung. Erstellen eines datengebundenen Steuerelements für ein Bytearrayelement im die **Datenquellen** Fenster, das ein Bild darstellt, müssen Sie das zu erstellende Steuerelement auswählen.  
  
Das folgende Verfahren geht davon aus, die die **Datenquellen** Fenster wird mit einem Element, das an das Bild gebundenen ist bereits aufgefüllt. 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>So binden Sie ein Bild in einer Datenbank an ein Steuerelement  
  
1.  Stellen Sie sicher, dass die Entwurfsoberfläche, der Sie das Steuerelement hinzufügen möchten, im WPF-Designer oder im Windows Forms-Designer geöffnet ist.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie die gewünschte Tabelle oder Objekt, sodass die Spalten bzw. Eigenschaften angezeigt.  
  
3.  Wählen Sie die Spalte oder die Eigenschaft aus, die die Bilddaten enthält, und wählen Sie eines der folgenden Steuerelemente aus der Dropdown-Steuerelementliste aus:  
  
    -   Wenn der WPF-Designer geöffnet ist, wählen Sie **Image**.  
  
    -   Wenn die Windows Forms-Designer geöffnet ist, wählen Sie **PictureBox-Steuerelement**.  
  
    -   Sie können auch ein anderes Steuerelement auswählen, das die Datenbindung unterstützt und Bilder anzeigen kann. Wenn das Steuerelement, das Sie verwenden möchten, nicht in der Liste der verfügbaren Steuerelemente ist, können Sie ihn der Liste hinzufügen und wählen Sie diese. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Siehe auch
[Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)