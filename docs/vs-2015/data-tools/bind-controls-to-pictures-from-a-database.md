---
title: Binden von Steuerelementen an Bilder aus einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fbaca836cb5b620c596b72bc991e91c1cfc2312c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189500"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Binden von Steuerelementen an Bilder aus einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können der **Datenquellen** Fenster aus, um ein Bild in einer Datenbank an ein Steuerelement in Ihrer Anwendung zu binden. Sie können z. B. ein Bild, das Binden einer <xref:System.Windows.Controls.Image> steuern, in einer WPF-Anwendung oder zu einer <xref:System.Windows.Forms.PictureBox> Steuerelement in Windows Forms-Anwendungen.  
  
 Bilder in einer Datenbank werden in der Regel als Bytearrays gespeichert. Elemente in der **Datenquellen** legen Sie Fenster, in dem gespeichert werden, da Bytearrays der Steuerelementtyp haben auf **keine** standardmäßig da Bytearrays, die von einem einfachen Bytearray bis zur ausführbaren Datei enthalten können einer großen Anwendung. Zum Erstellen eines datengebundenen Steuerelements für ein Bytearrayelement im der **Datenquellen** Fenster, das ein Bild darstellt, müssen Sie das zu erstellende Steuerelement auswählen.  
  
 Das folgende Verfahren setzt voraus, dass die **Datenquellen** Fenster wird mit einem Element, das an das Bild gebundenen ist bereits aufgefüllt. Weitere Informationen finden Sie unter [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>So binden Sie ein Bild in einer Datenbank an ein Steuerelement  
  
1.  Stellen Sie sicher, dass die Entwurfsoberfläche, der Sie das Steuerelement hinzufügen möchten, im WPF-Designer oder im Windows Forms-Designer geöffnet ist.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie die gewünschte Tabelle oder das Objekt, für die Spalten bzw. Eigenschaften angezeigt.  
  
3.  Wählen Sie die Spalte oder die Eigenschaft aus, die die Bilddaten enthält, und wählen Sie eines der folgenden Steuerelemente aus der Dropdown-Steuerelementliste aus:  
  
    -   Wenn der WPF-Designer geöffnet ist, wählen Sie **Image**.  
  
    -   Wenn der Windows Forms-Designer geöffnet ist, wählen Sie **PictureBox**.  
  
    -   Sie können auch ein anderes Steuerelement auswählen, das die Datenbindung unterstützt und Bilder anzeigen kann. Wenn das Steuerelement, das Sie verwenden möchten, nicht in der Liste der verfügbaren Steuerelemente ist, können Sie ihn zur Liste hinzufügen und wählen Sie ihn. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)

